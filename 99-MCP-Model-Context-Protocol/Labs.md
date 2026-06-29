# 99 - MCP - Labs

## Lab 1: Install a Public MCP Server
```bash
npm install -g @modelcontextprotocol/server-filesystem
# Add to Claude Desktop config (~/.config/claude/claude_desktop_config.json):
# {
#   "mcpServers": {
#     "filesystem": {
#       "command": "npx",
#       "args": ["-y", "@modelcontextprotocol/server-filesystem", "/allowed/path"]
#     }
#   }
# }
```
Then ask Claude: 'List files in my documents folder'
Claude should use the MCP filesystem tool.

## Lab 2: Build Security MCP Server
Build an MCP server with these 4 tools:
1. check_ip(ip) - queries AbuseIPDB API
2. check_hash(hash) - queries VirusTotal API
3. search_cve(keyword) - queries NVD API
4. decode_base64(encoded) - decodes base64 strings

Follow the structure from Notes.md. Test with MCP Inspector.

## Lab 3: MCP Security Audit
For each configured MCP server:
- [ ] List all exposed tools
- [ ] Maximum harm if each tool is misused?
- [ ] Input validation on tool parameters?
- [ ] Tool responses sanitized before returning to LLM?
- [ ] Audit logging for all tool calls?
- [ ] Can any tool response trigger prompt injection?
- [ ] What network access does the server have?

## Practice Challenges
- [ ] Build VirusTotal MCP server and connect to Claude Desktop
- [ ] Demonstrate indirect prompt injection via tool response
- [ ] Write security checklist for deploying an AI agent with MCP
- [ ] Read full MCP specification at modelcontextprotocol.io
