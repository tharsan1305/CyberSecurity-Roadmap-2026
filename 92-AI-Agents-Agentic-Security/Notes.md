# 92 - AI Agents & Agentic Security (MCP/Tool-use Risks)
## Overview
AI agents autonomously browse the web, run code, call APIs, and interact with external systems. This autonomy creates serious and novel security risks.

## 1. Agentic AI Architecture
```
User → Orchestrator (LLM) → Tool Calls → External Systems
             |
        Memory (short/long term)
             |
        Planning (ReAct, CoT)
```
Agent capabilities: web browsing, code execution, file R/W, API calls, email/calendar, database queries, spawning sub-agents.

## 2. Tool-Use and Function Calling Risks
| Risk | Description |
|------|-------------|
| Privilege escalation | Agent calls tools with more permissions than needed |
| Confused deputy | Agent tricked into using its permissions for attacker's benefit |
| Unintended data exfiltration | Agent sends sensitive data to attacker endpoint |
| Destructive actions | Agent deletes files, sends unauthorized emails, makes purchases |
| Infinite loops | Recursive tool calls exhaust compute resources |
| SSRF via agent | Agent fetches attacker-controlled URLs leaking internal data |

### Principle of Least Privilege for Agents
- Grant only tools the agent actually needs for the task
- Read-only access by default; write access requires justification
- Scope API keys to minimum required permissions
- Time-limited credentials; rotate after task completion

## 3. MCP (Model Context Protocol) Security
MCP is an open standard (Anthropic) for connecting LLMs to tools and data sources.

### MCP Security Risks
| Risk | Description | Mitigation |
|------|-------------|------------|
| Tool poisoning | Malicious MCP server provides harmful tools | Only use verified, signed servers |
| Prompt injection via MCP | Tool response contains hidden LLM instructions | Sanitize all tool outputs |
| Over-permissioned server | Server has broader access than needed | Least privilege on server |
| Unverified server | No identity verification for MCP server | Use server registries with signing |
| Data exfiltration | Server reads and leaks context window | Log and monitor all MCP calls |

### MCP Security Best Practices
- Review all tool definitions before connecting any MCP server
- Implement input and output validation on MCP responses
- Log every MCP tool call with parameters and responses
- Apply network isolation to limit MCP server reach
- Require human confirmation for any destructive or irreversible actions

## 4. Agent-to-Agent Communication Risks
- Multi-agent systems: one agent instructs another
- Compromised orchestrator can corrupt all sub-agents
- Agent messages can contain injected instructions
- Defense: authenticate agent messages, validate all instructions, human oversight checkpoints at critical steps
