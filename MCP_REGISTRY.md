# Publishing Glean MCP Server to the MCP Registry

This document outlines the process for publishing the Glean MCP Server to the Model Context Protocol (MCP) registry.

## Overview

The Glean MCP Server is listed in the MCP registry for discovery purposes. Users find the server in the registry, then follow our documentation to configure their organization-specific connection.

## Server Configuration

### server.json

The `server.json` file at the repository root defines our MCP server metadata. It follows the [official schema](https://static.modelcontextprotocol.io/schemas/2025-10-17/server.schema.json).

**Key fields:**

- `name`: `com.glean/mcp` - Our namespace identifier
- `description`: User-facing description of capabilities
- `title`: Display name ("Glean")
- `version`: Current version (update with each publish)
- `websiteUrl`: Points to setup documentation
- `icons`: Logo assets for display in MCP clients

**About the `remotes` section:**

The `remotes` section includes a placeholder URL (`https://acme-be.glean.com/mcp/default`) to enable one-click installation in MCP clients like VSCode. However, each organization has a unique Glean MCP server URL, so users must update this to their organization-specific endpoint after installation.

**Future improvement:** When the MCP registry supports URL template variables (schema 2025-12-11+), we will update to use `https://{instance}-be.glean.com/mcp/{server-name}` which will prompt users for their instance name during setup. The template version is saved in `server-2025-12-11.json` for when the mcp-publisher tool is updated to support the newer schema.

See the [generic server.json documentation](https://github.com/modelcontextprotocol/registry/blob/main/docs/reference/server-json/generic-server-json.md) for more details.

## Publishing Process

### Prerequisites

1. Install the MCP publisher CLI using one of these methods:

   **Homebrew (recommended):**
   ```bash
   brew install mcp-publisher
   ```

   **Binary download:**
   ```bash
   curl -L "https://github.com/modelcontextprotocol/registry/releases/latest/download/mcp-publisher_$(uname -s | tr '[:upper:]' '[:lower:]')_$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/').tar.gz" | tar xz mcp-publisher
   ```

2. Ensure you have:
   - Updated `version` in `server.json`
   - Access to the Glean domain private key (stored securely, contact DevOps/Security)
   - The private key in hex format (extracted from the PEM file)

### Authentication

Before publishing, authenticate using DNS-based verification:

```bash
mcp-publisher login dns \
  --domain glean.com \
  --private-key "<hex-encoded-private-key>"
```

To extract the hex-encoded private key from a PEM file:

```bash
# For Ed25519 keys:
openssl pkey -in key.pem -noout -text | grep -A3 "priv:" | tail -n +2 | tr -d ' :\n'

# For ECDSA P-384 keys:
openssl ec -in key.pem -noout -text | grep -A4 "priv:" | tail -n +2 | tr -d ' :\n'
```

**Security Notes:**

- The private key should be stored securely and never committed to version control
- Only authorized personnel should have access to perform registry publishes
- For CI/CD, store the hex-encoded private key as a secret (e.g., `MCP_PRIVATE_KEY`)


### Publish Command

```bash
mcp-publisher publish
```

The CLI will:

1. Validate your `server.json` against the schema
2. Verify namespace ownership (com.glean requires glean.com control)
3. Submit to `https://registry.modelcontextprotocol.io`
4. Return success or detailed error messages

### Common Errors

**"deprecated schema detected"**: The mcp-publisher version doesn't support the schema version in server.json. Update to the latest mcp-publisher or use an older schema version. Check the [schema changelog](https://github.com/modelcontextprotocol/registry/blob/main/docs/reference/server-json/CHANGELOG.md) for supported versions.

**"invalid remote URL"**: The URL in `remotes` contains unsupported characters or invalid format. Ensure the URL is a valid HTTPS endpoint.

**"namespace verification failed"**: Ensure you're authenticated with the correct domain and have access to the private key for glean.com.

## Where the Server Appears

After publishing:

1. **MCP Client Applications**: Users can discover and add Glean MCP Server from within:
   - Claude Desktop
   - Cursor
   - ChatGPT
   - Other MCP-compatible clients

2. **Third-Party Directories**: Sites like [MCPapps.net](https://mcpapps.net) may index and display the server

3. **GitHub Registry**: The server metadata is stored in the [modelcontextprotocol/registry](https://github.com/modelcontextprotocol/registry) repository

## Anthropic MCP Directory

To be included in [Anthropic's official MCP directory](https://support.claude.com/en/articles/11697096-anthropic-mcp-directory-policy), additional requirements apply:

### Pre-Submission Checklist

- [ ] Provide testing account with sample data for Anthropic verification
- [ ] Document 3+ working example prompts demonstrating core functionality
- [ ] Ensure all tools have required annotations (_readOnlyHint_, _destructiveHint_, _title_)
- [ ] Verify tool descriptions are narrow and unambiguous
- [ ] Confirm tool names are under 64 characters
- [ ] Review cross-service automation (if Glean Agents orchestrate multiple services)
- [ ] Privacy policy link accessible from documentation
- [ ] Support channels clearly documented
- [ ] Review and agree to [MCP Directory Terms](https://support.claude.com/en/articles/11697096-anthropic-mcp-directory-policy)

### Compliance Strengths

Glean MCP Server already meets most Anthropic requirements:

- **OAuth 2.0 authentication** with SSO integration
- **Permission-aware data access** via Knowledge Graph
- **Privacy guarantees** covered under Glean's DPA
- **Streamable HTTP transport** supported
- **Session management** via Glean Admin UI
- **No financial transactions, media generation, or IP infringement**

## Updating the Registry Entry

To publish an updated version:

1. Update the `version` field in `server.json`
2. Update any changed metadata (description, icons, etc.)
3. Run `mcp-publisher publish` again
4. The registry will update with the new version

## Documentation Requirements

Ensure the `websiteUrl` target (currently pointing to `docs.glean.com`) includes:

- Clear setup instructions for getting organization-specific URLs
- Environment variable requirements (GLEAN_INSTANCE, etc.)
- Authentication setup (OAuth or API tokens)
- Troubleshooting guide
- Example use cases and prompts

## Resources

- [MCP Registry Documentation](https://github.com/modelcontextprotocol/registry)
- [server.json Schema](https://static.modelcontextprotocol.io/schemas/2025-10-17/server.schema.json)
- [Generic server.json Format](https://github.com/modelcontextprotocol/registry/blob/main/docs/reference/server-json/generic-server-json.md)
- [Official Registry Requirements](https://github.com/modelcontextprotocol/registry/blob/main/docs/reference/server-json/official-registry-requirements.md)
- [Anthropic MCP Directory Policy](https://support.claude.com/en/articles/11697096-anthropic-mcp-directory-policy)
- [Glean MCP Server Documentation](https://docs.glean.com/administration/platform/mcp/about)

## Maintenance

- Review server.json quarterly for accuracy
- Update version with each significant feature release
- Monitor for registry policy changes
- Track user feedback from MCP client integrations
