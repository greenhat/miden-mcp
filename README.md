# Miden MCP Server

This project implements a Model Context Protocol (MCP) server that interacts with Miden developer tools. 

## Setup

To run the Miden MCP server using npx, use the following command:

```bash
npx -y @miden/mcp@latest
```

## Usage with Cursor or Claude Desktop

Add the following configuration. For more information, read the [Cursor MCP documentation](https://docs.cursor.com/context/model-context-protocol) or the [Claude Desktop MCP guide](https://modelcontextprotocol.io/quickstart/user).

```json
{
  "mcpServers": {
    "miden-mcp": {
      "command": "npx",
      "args": ["-y", "@miden/mcp@latest"]
    }
  }
}
```

On Windows, you might need to use this alternative configuration:

```json
{
  "mcpServers": {
    "miden-mcp": {
      "command": "cmd",
      "args": ["/k", "npx", "-y", "@miden/mcp@latest"]
    }
  }
}
```

## Available tools

This MCP server provides the following tools:

| Tool Name               | Description                                    |
| ----------------------- | ---------------------------------------------- |
| search_dev_docs         | Search Miden developer documentation               |

## Development

The server is built using the MCP SDK.

1. `npm install`
1. Modify source files
1. Run `npm run build` to compile
1. Run `npm run test` to run tests
1. Add an MCP server that runs this command: `node <absolute_path_of_project>/dist/index.js`

## License

MIT

## Example

Here is the log of the chat with Claude Sonnet 3.7 using `miden-mcp` - https://gist.github.com/greenhat/3c46e4b8ca850639392c1c03b2ae0c7a
See that even one tool call to `miden-mcp` is enough to provide the context to the LLM to generate a correct answer.
