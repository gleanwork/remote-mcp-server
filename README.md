<p align="center">
  <img src="./glean-logo.svg" alt="Glean Logo" width="200">
</p>

<h1 align="center">Glean Remote MCP Server</h1>

<p align="center">
  <a href="https://docs.glean.com/administration/platform/mcp/about" target="_blank">Documentation</a> |
  <a href="https://docs.glean.com/administration/platform/mcp/enable-mcp-servers" target="_blank">Setup Guide</a> |
  <a href="https://registry.modelcontextprotocol.io" target="_blank">MCP Registry</a>
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
