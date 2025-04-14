---
sidebar_position: 2
---

# How to use

You can use our MCP server with any client that supports MCP servers using SSE communication with header support. Currently, our recommended option is VS Code. Below, you'll find a sample configuration to help you get started.


## Configuration for Visual Studio Code
To establish a connection with an MCP server, the `X-MCP-AUTH-TOKEN` header is required.

Below is an example .vscode/settings.json configuration for Visual Studio Code:

```
{
    "mcp": {
        "inputs": [],
        "servers": {
            "hedera": {
                "type": "sse",
                "url": "http://localhost:3000/sse",
                "headers": { "X-MCP-AUTH-TOKEN": "your-mcp-auth-token"}
            }
        }
    }
}
```

Note: Currently, passing additional headers (such as `X-MCP-AUTH-TOKEN`) is not supported in Cursor IDE.
Source: [Cursor Forum](https://forum.cursor.com/t/api-key-for-sse-mcp-servers/63300)
However, MCP integration is evolving rapidly, and support for custom headers is expected to be added in future versions of Cursor and other MCP Client Tools.
