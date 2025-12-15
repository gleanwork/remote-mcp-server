<p align="center">
  <img src="https://developers.glean.com/img/glean-text.svg" alt="Glean Logo" width="200">
</p>

<h1 align="center">Glean Remote MCP Server</h1>

<p align="center">
  <a href="https://docs.glean.com/administration/platform/mcp/about" target="_blank">Documentation</a> |
  <a href="https://docs.glean.com/administration/platform/mcp/enable-mcp-servers" target="_blank">Setup Guide</a> |
  <a href="https://registry.modelcontextprotocol.io" target="_blank">MCP Registry</a>
</p>

<p align="center">
  <a href="https://registry.modelcontextprotocol.io"><img src="https://badge.mcpx.dev?type=server" alt="MCP Server"></a>
  <a href="https://github.com/gleanwork/.github/blob/main/docs/repository-stability.md#ga"><img src="https://img.shields.io/badge/-GA-F6F3EB?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMzIgMzIiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxwYXRoIGQ9Ik0yNC4zMDA2IDIuOTU0MjdMMjAuNzY1NiAwLjE5OTk1MUwxNy45MDI4IDMuOTk1MjdDMTMuNTY1MyAxLjkzNDk1IDguMjMwMTkgMy4wODQzOSA1LjE5Mzk0IDcuMDA5ODNDMS42NTg4OCAxMS41NjQyIDIuNDgzIDE4LjExMzggNy4wMzczOCAyMS42NDg5QzguNzcyMzggMjIuOTkzNSAxMC43ODkzIDIzLjcwOTIgMTIuODI3OSAyMy44MTc3QzE2LjE0NjEgMjQuMDEyOCAxOS41MDc3IDIyLjYyNDggMjEuNjc2NSAxOS44MDU1QzI0LjczNDQgMTUuODggMjQuNTE3NSAxMC40MTQ4IDIxLjQ1OTYgNi43Mjc4OUwyNC4zMDA2IDIuOTU0MjdaTTE4LjExOTcgMTcuMDUxMkMxNi4xMDI4IDE5LjYzMiAxMi4zNzI1IDIwLjEwOTEgOS43NzAwMSAxOC4wOTIyQzcuMTg5MTkgMTYuMDc1MiA2LjcxMjA3IDEyLjMyMzMgOC43MjkwMSA5Ljc0MjQ2QzkuNzA0OTQgOC40ODQ1OCAxMS4xMTQ2IDcuNjgyMTQgMTIuNjc2MSA3LjQ4Njk2QzEzLjA0NDggNy40NDM1OCAxMy40MTM1IDcuNDIxOSAxMy43ODIyIDcuNDQzNThDMTQuOTc1IDcuNTA4NjUgMTYuMTI0NCA3Ljk0MjM5IDE3LjA3ODcgOC42Nzk3N0MxOS42NTk1IDEwLjcxODQgMjAuMTM2NiAxNC40NzAzIDE4LjExOTcgMTcuMDUxMloiIGZpbGw9IndoaXRlIi8+CjxwYXRoIGQ9Ik0yNC41MTc2IDIxLjY5MjJDMjMuOTMyIDIyLjQ1MTMgMjMuMjgxNCAyMy4xMjM2IDIyLjU2NTcgMjMuNzUyNUMyMS44NzE3IDI0LjMzODEgMjEuMTEyNyAyNC44ODAzIDIwLjMxMDIgMjUuMzM1N0MxOS41Mjk1IDI1Ljc2OTUgMTguNjgzNyAyNi4xMzgyIDE3LjgzNzggMjYuNDIwMUMxNi45OTIgMjYuNzAyIDE2LjEwMjggMjYuODk3MiAxNS4yMTM3IDI3LjAwNTdDMTQuMzI0NSAyNy4xMTQxIDEzLjQzNTMgMjcuMTU3NSAxMi41MjQ0IDI3LjA5MjRDMTEuNjEzNSAyNy4wMjczIDEwLjcyNDMgMjYuODc1NSA5Ljg1Njg0IDI2LjY1ODdMOS42NjE2NSAyNy4zNzQzTDguNzcyNDYgMzAuOTk2MkM5LjkwMDIxIDMxLjI5OTggMTEuMDQ5NyAzMS40NzMzIDEyLjIyMDggMzEuNTZDMTIuMjY0MiAzMS41NiAxMi4zMjkyIDMxLjU2IDEyLjM3MjYgMzEuNTZDMTMuNTAwMyAzMS42MjUxIDE0LjY0OTggMzEuNTgxNyAxNS43NTU4IDMxLjQ1MTZDMTYuOTI3IDMxLjI5OTggMTguMDk4MSAzMS4wMzk1IDE5LjIyNTggMzAuNjcwOEMyMC4zNTM2IDMwLjMwMjIgMjEuNDU5NyAyOS44MjUgMjIuNTAwNyAyOS4yMzk1QzIzLjU2MzQgMjguNjUzOSAyNC41NjEgMjcuOTM4MiAyNS40OTM1IDI3LjE1NzVDMjYuNDQ3OCAyNi4zNTUgMjcuMzE1MyAyNS40NDQyIDI4LjA3NDQgMjQuNDQ2NUMyOC4xODI4IDI0LjMxNjQgMjguMjY5NSAyNC4xNjQ2IDI4LjM3OCAyNC4wMTI4TDI0Ljc3NzkgMjEuMzQ1MkMyNC42Njk0IDIxLjQ1MzcgMjQuNjA0NCAyMS41ODM4IDI0LjUxNzYgMjEuNjkyMloiIGZpbGw9IndoaXRlIi8+Cjwvc3ZnPg==&labelColor=343CED" alt="GA"></a>
</p>

---

Remote MCP Server that securely connects Glean Enterprise Knowledge with your IDE, LLM, or agent platform of choice.

## Overview

The Glean MCP Server implements the [Model Context Protocol](https://modelcontextprotocol.io) to provide AI assistants and developer tools with secure, real-time access to your organization's enterprise knowledge. It enables natural language interaction with company documents, people, and data while respecting existing access permissions.

## Features

- **Enterprise Knowledge Access** - Search and retrieve information from your company's documents, wikis, and knowledge bases
- **People & Expertise Discovery** - Find colleagues, understand org structure, and identify subject matter experts
- **Permission-Aware** - All data access respects your organization's existing access controls
- **OAuth 2.0 Authentication** - Secure authentication with SSO integration
- **Streamable HTTP Transport** - Modern, efficient protocol for real-time communication

## Getting Started

Each organization has a unique Glean MCP server URL. To set up the Glean MCP Server for your organization:

**[View the Setup Guide](https://docs.glean.com/administration/platform/mcp/enable-mcp-servers)**

The guide covers:

- Obtaining your organization's MCP server URL
- Configuring your MCP client (Claude Desktop, Cursor, etc.)
- Authentication setup
- Available tools and example prompts

## Compatibility

The Glean MCP Server works with any MCP-compatible client. See the [full list of supported hosts](https://docs.glean.com/user-guide/mcp/usage#supported-hosts) for details.

## Documentation

- [About Glean MCP Server](https://docs.glean.com/administration/platform/mcp/about)
- [Enable MCP Servers](https://docs.glean.com/administration/platform/mcp/enable-mcp-servers)
- [MCP Tools Reference](https://docs.glean.com/administration/platform/mcp/about#available-tools)

## Support

- **Documentation**: [docs.glean.com](https://docs.glean.com/administration/platform/mcp/about)
- **Issues**: For bugs or feature requests related to the Glean MCP Server, please contact Glean support through your organization's support channel

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
