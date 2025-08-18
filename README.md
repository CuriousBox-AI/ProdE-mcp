# ProdE MCP Server

**[ProdE](https://prode.ai)** |**[Documentation](https://docs.prode.ai)** | **Free access to all ProdE features for first month**

*ProdE is your 24x7 available production engineer, a multi-repository AI coding assistant that understands your entire codebase ecosystem, not just individual files.*

## What is ProdE MCP Server?

ProdE MCP Server bridges the gap between your codebase and AI coding assistants by providing deep contextual understanding of your repositories. Instead of working with generic code suggestions, get AI responses that understand your specific project structure, patterns, and history across multiple codebases.
 
## Key Features

- **Cross-Repository Insights**: Query across multiple codebases simultaneously
- **Improved AI Accuracy**: AI understands your project structure and patterns
- **Contextual Code Understanding**: AI assistance based on your actual codebase, not generic examples
- **Secure Integration**: Token-based authentication with encrypted communication
- **Wide Tool Compatibility**: Supports 8+ popular coding assistants and editors

## Use Cases

### 1. **Multi-Repository Onboarding & System Understanding**
**Example**: A new developer joins your team and needs to understand how user authentication flows through your 15+ microservices across frontend, backend, and mobile repositories.

**What ProdE does**: Simultaneously analyzes authentication patterns across all repositories in your knowledge layer to provide a complete cross-service authentication flow explanation.

### 2. **Cross-Repository API Integration Discovery**
**Example**: You're building a feature that needs to integrate with internal APIs scattered across different team repositories, but documentation is outdated or missing.

**What ProdE does**: Searches across all connected repositories to find current API definitions, real usage examples, and integration patterns from multiple services in one query.

### 3. **Multi-Repo Impact Analysis for Refactoring**
**Example**: You need to refactor a shared utility library used across 20+ repositories, but want to understand all usage patterns and potential breaking changes.

**What ProdE does**: Analyzes usage patterns across all repositories simultaneously to identify every implementation, dependency, and similar code that could be affected by your changes.

### 4. **Distributed System Bug Investigation**
**Example**: A production issue involves data flow through multiple services (payment-service, user-service, notification-service, audit-service), and you need to trace the complete request lifecycle.

**What ProdE does**: Connects the dots between all involved repositories to map the complete data flow, error handling, and logging patterns across your entire distributed system.

### 5. **Cross-Project Architecture Pattern Analysis**
**Example**: You're implementing caching for a new service and want to see what caching strategies, configurations, and patterns your team has successfully used across different projects.

**What ProdE does**: Analyzes caching implementations across all repositories in your knowledge layer to show proven patterns, configuration examples, and architectural decisions from your entire codebase ecosystem.

## Available Tools

The ProdE MCP server provides the following tools:

- `get_all_repositories` - Retrieve information about all repositories in your knowledge layer
- `ask_specific_codebase` - Ask questions about a specific repository/codebase
- `ask_all_codebases` - Ask questions across all your repositories

## Supported Coding Assistants

| Tool | Protocol | Configuration File | Status |
|------|----------|-------------------|--------|
| [Cursor](https://cursor.sh/) | `streamable-http`, `deeplink` | `~/.cursor/mcp.json` | ✅ Supported |
| [Cline](https://github.com/cline/cline) | `streamable-http` | `cline_mcp_settings.json` | ✅ Supported |
| [VS Code (GitHub Copilot)](https://code.visualstudio.com/) | `streamable-http` | `.vscode/mcp.json` | ✅ Supported |
| [Windsurf](https://windsurf.com/) | `SSE` | `~/.codeium/windsurf/mcp_config.json` | ✅ Supported |
| [Augment Code](https://augmentcode.com/) | `command-based` | `settings.json` | ✅ Supported |
| [RooCode](https://roocode.com/) | `streamable-http` | `mcp_settings.json` | ✅ Supported |
| [Gemini CLI](https://ai.google.dev/gemini-api/docs/cli) | `HTTP URL` | `~/.gemini/settings.json` | ✅ Supported |
| [OpenHands](https://github.com/All-Hands-AI/OpenHands) | `stdio` | MCP Configuration UI | ✅ Supported (Local only) |

## Quick Start

### 1. Connect to Git Provider

1. Sign up for a [ProdE account](https://prode.ai)
2. Connect your git provider:
   - **GitHub** ✅ Supported
   - **Bitbucket** ✅ Supported
   - **GitLab** 🚧 Coming soon
3. Authorize ProdE to Read-only access of your repositories

### 2. Add Repositories to Knowledge Layer

1. Browse your available repositories
2. Select the repositories you want to add to your knowledge layer
3. ProdE will analyze and index your selected codebases for contextual understanding

### 3. Get Your MCP Authentication Token

1. Navigate to **MCP Settings** in your dashboard
2. Copy your authentication token
3. This token will be used to connect your coding assistant to the ProdE MCP server

### 4. Choose Your Integration

Select your preferred coding assistant from the supported tools above and follow the specific setup instructions.

## Configuration Examples

### Cursor (Recommended - One-Click Setup)

**Option A: Deep Link (Automatic)**
Simply click the "Connect with Cursor" button in your ProdE dashboard for automatic setup.

**Option B: Manual Configuration**
```json
{
  "mcpServers": {
    "prode-codebase-understanding": {
      "type": "streamable-http",
      "url": "https://api.prode.ai/code-parsing/v1/mcp/",
      "note": "The mcp server provides codebase understanding by prode.",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN_HERE"
      }
    }
  }
}
```

### VS Code with GitHub Copilot

Create `.vscode/mcp.json` in your project root:

```json
{
  "servers": {
    "prode-codebase-understanding": {
      "type": "http",
      "url": "https://api.prode.ai/code-parsing/v1/mcp/",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN_HERE"
      }
    }
  }
}
```

### Cline

Create `cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "prode-codebase-understanding": {
      "name": "Prode Codebase Understanding",
      "type": "streamableHttp",
      "url": "https://api.prode.ai/code-parsing/v1/mcp/",
      "note": "The mcp server provides codebase understanding by prode.",
      "headers": {
        "Authorization": "Bearer YOUR_TOKEN_HERE"
      },
      "alwaysAllow": ["get_all_repositories", "ask_specific_codebase", "ask_all_codebases"],
      "disabled": false
    }
  }
}
```

### Windsurf

Create `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "prode-codebase-understanding": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://api.prode.ai/code-parsing/v1/mcp/",
        "--header",
        "Authorization: Bearer YOUR_TOKEN_HERE"
      ]
    }
  }
}
```

### OpenHands (Local Only)

Add to MCP configuration in OpenHands settings:

```json
{
  "sse_servers": [],
  "stdio_servers": [
    {
      "name": "prode-codebase-understanding",
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://api.prode.ai/code-parsing/v1/mcp/",
        "--header",
        "Authorization: Bearer YOUR_TOKEN_HERE"
      ],
      "env": {}
    }
  ],
  "shttp_servers": []
}
```

## Prerequisites

### All Integrations
- Active ProdE account with repositories in knowledge layer
- Valid authentication token from ProdE dashboard

## Support

- **Documentation**: [https://docs.prode.ai](https://docs.prode.ai)
- **Community**: Join our [discord community](https://discord.gg/uxPgzg6BwZ) for support and updates

## License

This project is licensed under the terms specified by ProdE. Please refer to [License](./LICENSE)

---

**Ready to enhance your coding experience?** Get started by [signing up for ProdE](https://prode.ai) and connecting your first repository to the knowledge layer.

---
[![MCP Badge](https://lobehub.com/badge/mcp/curiousbox-ai-prode-mcp)](https://lobehub.com/mcp/curiousbox-ai-prode-mcp)
[![smithery badge](https://smithery.ai/badge/@CuriousBox-AI/prode-mcp)](https://smithery.ai/server/@CuriousBox-AI/prode-mcp)