# Claude MCP Server Builder

> Build ready-to-use MCP servers for Claude Desktop with ready-to-use system prompts and workflows

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude](https://img.shields.io/badge/Claude-Desktop-blue)](https://claude.ai/download)
[![MCP](https://img.shields.io/badge/MCP-Protocol-green)](https://modelcontextprotocol.io/)

Stop wrestling with MCP server configuration, path problems, and setup. This repository provides comprehensive system instructions that enable Claude (or any LLM) to guide you through building your first (of many) MCP servers.

## ✨ Features

- **🧪 Test-Driven Development** - Validate APIs before building MCP servers
- **⚡ FastMCP-First** - Use the fastest path for 90% of use cases
- **📁 Flat Structure** - Simple project layout that scales when needed
- **🔄 Local Testing** - Test tools without Claude Desktop restarts
- **📚 Production Patterns** - Based on real servers with 50+ tools in production
- **🎯 Step-by-Step Guidance** - Claude walks you through every stage

## 🚀 Quick Start

Get your first MCP server running in **2-4 hours**:

1. **Create Claude Project** (2 min)
   ```
   Open Claude.ai → Projects → Create Project → "MCP Server Builder"
   ```

2. **Add System Instructions** (2 min)
   - Copy [`docs/SYSTEM_INSTRUCTIONS.md`](docs/SYSTEM_INSTRUCTIONS.md)
   - Paste into Project's "Custom Instructions"
   - Save

3. **Start Building** (1 min)
   ```
   I want to build an MCP server for [YOUR_SERVICE].
   
   Service details:
   - Type: [REST API / Database / SaaS]
   - Authentication: [API key / OAuth / etc]
   - Key operations: [list 3-5 things]
   
   Let's start with test_client.py.
   ```

That's it! Claude guides you through the rest.

**👉 [Full Quick Start Guide →](QUICKSTART.md)**

## 📋 What You Get

### Core Documentation

| File | Purpose | Size |
|------|---------|------|
| **[QUICKSTART.md](QUICKSTART.md)** | Get started in 5 minutes | 5 min read |
| **[docs/SYSTEM_INSTRUCTIONS.md](docs/SYSTEM_INSTRUCTIONS.md)** | Complete system prompt (900 lines) | Complete guide |
| **[docs/USER_PROMPT_TEMPLATE.md](docs/USER_PROMPT_TEMPLATE.md)** | Copy-paste prompt templates | Quick reference |
| **[docs/PROJECT_SETUP.md](docs/PROJECT_SETUP.md)** | Detailed project configuration | Deep dive |

### Templates & Tools

- **[templates/](templates/)** - Starter files for your MCP projects
- Includes: `.env.example`, `.gitignore`, `requirements.txt`, project quickstart template

## 🎯 The Workflow

```
┌─────────────────┐
│  test_client.py │  ← Test API authentication & operations
└────────┬────────┘
         │ ✅ Pass
         ▼
┌─────────────────┐
│   Build Server  │  ← Create MCP server with FastMCP
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  test_server.py │  ← Test MCP tools locally
└────────┬────────┘
         │ ✅ Pass
         ▼
┌─────────────────┐
│ Claude Desktop  │  ← Full integration
└─────────────────┘
```

**Key Principle:** Never build what you haven't tested.

## 💡 Use Cases

Build MCP servers for:

### REST APIs
- Data services (Fivetran, Census, dbt, Snowflake, Databricks, Google Cloud, AWS, Azure)
- Payment processing (Stripe, PayPal)
- Communication (Twilio, SendGrid)
- Project management (Jira, Linear, Asana)
- Custom internal APIs

### Databases
- PostgreSQL
- MySQL
- Snowflake
- BigQuery
- MongoDB

### SaaS Platforms
- GitHub
- Slack
- Notion
- Google Workspace
- Microsoft 365

## 🎓 Example: Building a Weather MCP Server

```
You: I want to build an MCP server for OpenWeatherMap API.

Service details:
- Type: REST API
- Authentication: API key
- Key operations:
  1. Get current weather
  2. Get 5-day forecast
  3. Search cities

Let's start with test_client.py.

Claude: [Creates test_client.py with OpenWeatherMap API...]
```

**Result:** Working MCP server in 2-3 hours with proper testing and error handling.

## 🏗️ What Makes This Different

### Traditional Approach ❌
1. Start coding immediately
2. Fight with paths and configs
3. Debug in Claude Desktop (slow)
4. Write documentation (that becomes outdated)
5. Realize you need to refactor

### This Approach ✅
1. Test API first (`test_client.py`)
2. Build incrementally (MVP → expand)
3. Test locally (`test_server.py`)
4. Configure Claude Desktop (once the MCP Server works)
5. Document after success

## 📊 Testing Philosophy

### Three-Phase Testing

1. **test_client.py** - API validation
   - Authenticates successfully
   - Makes actual API calls
   - Handles errors gracefully
   - Provides actionable feedback

2. **test_server.py** - Tool validation
   - Tests MCP tools directly
   - Validates JSON responses
   - Checks error handling
   - No Claude Desktop required

3. **Claude Desktop** - Integration
   - Full end-to-end testing
   - Natural language interface
   - Production validation

## 🛠️ Technology Stack

### Supported Languages
- **Python** (FastMCP recommended)
- **TypeScript/Node.js** (Official MCP SDK)

### Key Dependencies
- FastMCP - Rapid MCP server development
- python-dotenv - Environment management
- requests/httpx - API communication

### Requirements
- Python 3.10+ or Node.js 18+
- Claude Desktop
- API credentials for services you're integrating

## 📚 Documentation

### Getting Started
1. [Quick Start Guide](QUICKSTART.md) - 5 minutes to first prompt
2. [System Instructions](docs/SYSTEM_INSTRUCTIONS.md) - Complete guide
3. [Project Setup](docs/PROJECT_SETUP.md) - Detailed configuration

### Reference
- [User Prompt Templates](docs/USER_PROMPT_TEMPLATE.md) - Copy-paste prompts
- [Templates Directory](templates/) - Starter files

### External Resources
- [MCP Protocol Specification](https://modelcontextprotocol.io/)
- [Claude Desktop Download](https://claude.ai/download)
- [FastMCP Documentation](https://github.com/jlowin/fastmcp)

## 🤝 Contributing

Contributions welcome! Here's how you can help:

- **Share your patterns** - Built an interesting MCP server? Share it!
- **Improve documentation** - Found something unclear? Submit a PR!
- **Report issues** - Something not working? Open an issue!
- **Add examples** - Built something cool? Add it to `examples/`

### Contribution Guidelines

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-pattern`)
3. Commit your changes (`git commit -m 'Add amazing pattern'`)
4. Push to the branch (`git push origin feature/amazing-pattern`)
5. Open a Pull Request

## 🗺️ Roadmap

### Current (v1.0)
- ✅ Complete system instructions
- ✅ Test-driven workflow
- ✅ FastMCP-first approach
- ✅ Comprehensive documentation

### Planned
- 📋 Example implementations
- 📋 Video walkthrough tutorials
- 📋 Troubleshooting database
- 📋 Community patterns repository
- 📋 Advanced orchestration guides

## 💬 Community & Support

- **Questions?** Open a [GitHub Discussion](https://github.com/YOUR_USERNAME/claude-mcp-server-builder/discussions)
- **Issues?** Submit a [GitHub Issue](https://github.com/YOUR_USERNAME/claude-mcp-server-builder/issues)

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built on patterns from production MCP servers
- Inspired by the Model Context Protocol community
- Powered by Claude and FastMCP
- Thanks to all contributors and early adopters

## ⭐ Show Your Support

If this project helped you build better MCP servers, give it a star! ⭐

It helps others discover these patterns and encourages continued development.

---

**Ready to build?** Start with the [Quick Start Guide](QUICKSTART.md) →

**Questions?** Check the [Documentation](docs/)