# 99 - MCP (Model Context Protocol)
## Overview
MCP is an open standard by Anthropic for connecting LLMs to tools and data sources in a standardized way.

## MCP vs APIs
| | MCP | Traditional API |
|--|-----|-----------------|
| Discovery | Server advertises tools | Manual documentation |
| Protocol | Standardized JSON-RPC | Varies per API |
| Context | Full conversation context | Stateless |
| Integration | Plug-and-play | Custom per API |

## Architecture
```
MCP Client (Claude / your app)
    <-> MCP Protocol (JSON-RPC over stdio or SSE)
MCP Server (exposes tools and resources)
    <-> External Systems (files, DBs, APIs)
```

## Components
- **Tools**: Functions the LLM can call (check_ip, search_logs, create_ticket)
- **Resources**: Data the LLM can read (files, DB records, docs)
- **Prompts**: Reusable prompt templates

## MCP Security Risks
| Risk | Description | Mitigation |
|------|-------------|------------|
| Tool poisoning | Malicious server provides harmful tools | Only use verified servers |
| Prompt injection via MCP | Tool response has hidden LLM instructions | Sanitize all tool outputs |
| Over-permissioned server | Server has broader access than needed | Least privilege |
| Unverified server | No identity verification | Use signed registries |
| Data exfiltration | Server reads and leaks context | Log and monitor all calls |

## Building an MCP Server (Python)
```python
from mcp.server import Server
import mcp.server.stdio
import mcp.types as types
import asyncio

server = Server('security-tools')

@server.list_tools()
async def list_tools():
    return [types.Tool(
        name='check_ip',
        description='Check IP reputation on AbuseIPDB',
        inputSchema={'type':'object','properties':{'ip':{'type':'string'}},'required':['ip']}
    )]

@server.call_tool()
async def call_tool(name, arguments):
    if name == 'check_ip':
        ip = arguments['ip']
        # Call AbuseIPDB API here
        return [types.TextContent(type='text', text=f'IP {ip}: reputation score 85/100')]

async def main():
    async with mcp.server.stdio.stdio_server() as (r,w):
        await server.run(r, w)

asyncio.run(main())
```
