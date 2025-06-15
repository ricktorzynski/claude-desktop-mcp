# Claude Desktop MCP Integration


Repository to set up example L9 from [MCP: Build Rich-Context AI Apps with Anthropic](https://learn.deeplearning.ai/courses/mcp-build-rich-context-ai-apps-with-anthropic) short course on Deeplearning.ai.

## Difficulties

One difficulty in setting this up was getting the claude_desktop_config.json to work with project in WSL2 Ubuntu.  Here is the solution I found:

```
{
  "mcpServers": {
    "filesystem": {
      "command": "wsl.exe",
      "args": [
        "bash",
        "-c",
        "npx -y @modelcontextprotocol/server-filesystem /home/rick/anthropic_mcp"
      ]
    },
    "research": {
      "command": "wsl.exe",
      "args": [
        "bash",
        "-c",
        "/home/rick/.local/bin/uv --directory /home/rick/anthropic_mcp run research_server.py"
      ]
    },
    "fetch": {
      "command": "wsl.exe",
      "args": [
        "bash",
        "-c",
        "/home/rick/.local/bin/uvx mcp-server-fetch"
      ]
    }
  }
}
```