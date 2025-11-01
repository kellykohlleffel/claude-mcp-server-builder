# MCP Server Builder for Claude Desktop

> Build production-ready MCP servers for Claude Desktop with comprehensive system prompts and test-driven workflows

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude](https://img.shields.io/badge/Claude-Desktop-blue)](https://claude.ai/download)
[![MCP](https://img.shields.io/badge/MCP-Protocol-green)](https://modelcontextprotocol.io/)

This repository provides comprehensive system instructions that enable Claude (or any LLM that supports a projects approach) to guide you through building production-ready MCP servers with agent-centric design and optional token optimization.

## ✨ Features

- **🎯 Agent-Centric Design** - Workflow-oriented tools that minimize Claude's orchestration burden
- **🧪 Test-Driven Development** - Validate APIs before building MCP servers
- **⚡ FastMCP-First** - Use the fastest path for 90% of use cases
- **📁 Flat Structure** - Simple project layout that scales when needed
- **🔄 Local Testing** - Test tools without Claude Desktop restarts
- **⚡ Token Optimization** - Optional patterns for workflow servers (90-99% reduction)
- **📊 Token Transparency** - Self-reporting for optimized servers
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
   - Usage pattern: [How often will this be called?]
   
   Let's start with test_client.py.
   ```

That's it! Claude guides you through the rest.

**👉 [Full Quick Start Guide →](QUICKSTART.md)**

## 📋 What You Get

### Core Documentation

| File | Purpose | Size |
|------|---------|------|
| **[QUICKSTART.md](QUICKSTART.md)** | Get started in 5 minutes | 5 min read |
| **[docs/SYSTEM_INSTRUCTIONS.md](docs/SYSTEM_INSTRUCTIONS.md)** | Complete system prompt | Complete guide |
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
│   Build Server  │  ← Create MCP server with agent-centric tools
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  test_server.py │  ← Test MCP tools locally
└────────┬────────┘
         │ ✅ Pass
         ▼
┌─────────────────┐
│test_token_usage │  ← Optional: Measure tokens (workflow servers)
└────────┬────────┘
         │ ✅ Pass
         ▼
┌─────────────────┐
│ Claude Desktop  │  ← Full integration
└─────────────────┘
```

**Key Principles:**
- Never build what you haven't tested
- Design for workflows, not API endpoints
- Optimize when it matters (workflow servers)

## 💡 Design Philosophy

### Agent-Centric vs API-Centric

**❌ API-Centric (Avoid):**
```python
list_databases()
list_schemas(database)
list_tables(database, schema)
# User: "What's in my warehouse?" → 10-50+ tool calls
```

**✅ Agent-Centric (Build This):**
```python
discover_data_warehouse(resource_type, search_term, filters)
# User: "What's in my warehouse?" → 1 tool call
```

### When to Optimize

**Standard Approach:**
- Simple single-API wrappers
- Infrequent usage (<5 calls/conversation)
- Small responses (<1000 tokens)

**Token Optimization:**
- Workflow servers (orchestrating multiple APIs)
- Frequent usage (>10 calls/conversation)
- Large responses (>5000 tokens)
- Making efficiency claims

**The system instructions guide you on when to apply each approach.**

## 🎓 Use Cases

Build MCP servers for:

### REST APIs
- **Data Platform**: Fivetran, Census, dbt Cloud, Hightouch
- **Data Warehouses**: Snowflake, Databricks, BigQuery
- **Cloud Services**: AWS, GCP, Azure
- **Workflow**: Jira, Linear, Asana, Monday
- **Communication**: Slack, Twilio, SendGrid
- **Custom APIs**: Your internal services

### Databases
- PostgreSQL, MySQL, Snowflake, BigQuery, MongoDB
- With agent-centric query tools

### SaaS Platforms
- GitHub, GitLab, Bitbucket
- Google Workspace, Microsoft 365
- Notion, Confluence, SharePoint

### Workflow Servers
- Pipeline health monitors
- Cross-service orchestrators
- Multi-stage data workflows
- (With built-in token optimization)

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
- Usage: Checking weather 5-10 times per conversation

Let's start with test_client.py.

Claude: [Creates test_client.py with OpenWeatherMap API...]
        [Guides through agent-centric tool design...]
        [Consolidates related operations...]
```

**Result:** Working MCP server in 2-3 hours with:
- 3-5 agent-centric tools (not 10+ API-centric tools)
- Proper testing and error handling
- Optional optimization if needed

## 🏗️ What Makes This Different

### Traditional Approach ❌
1. Start coding immediately
2. Wrap every API endpoint as a tool
3. Fight with paths and configs
4. Debug in Claude Desktop (slow)
5. Users need 10+ tool calls for simple tasks
6. Write documentation (that becomes outdated)
7. Realize you need to refactor

### This Approach ✅
1. Test API first (`test_client.py`)
2. Design agent-centric tools (workflows, not endpoints)
3. Build incrementally (MVP → expand)
4. Test locally (`test_server.py`)
5. Users accomplish tasks in 1-2 tool calls
6. Configure Claude Desktop (once it works)
7. Optional: Optimize and verify token usage
8. Document after success

## 📊 Testing Philosophy

### Three (or Four) Phase Testing

1. **test_client.py** - API validation
   - Authenticates successfully
   - Makes actual API calls
   - Handles errors gracefully
   - Tests both full and lightweight methods (if optimizing)

2. **test_server.py** - Tool validation
   - Tests MCP tools directly
   - Validates JSON responses
   - Checks error handling
   - Verifies tool consolidation works
   - No Claude Desktop required

3. **test_token_usage.py** - Token measurement (optional, for workflow servers)
   - Measures actual token consumption
   - Validates optimization claims
   - Provides per-component breakdown
   - Enables data-driven decisions

4. **Claude Desktop** - Integration
   - Full end-to-end testing
   - Natural language interface
   - Production validation
   - Real-world workflow testing

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
2. [System Instructions](docs/SYSTEM_INSTRUCTIONS.md) - Complete guide with agent-centric patterns
3. [Project Setup](docs/PROJECT_SETUP.md) - Detailed configuration

### Reference
- [User Prompt Templates](docs/USER_PROMPT_TEMPLATE.md) - Copy-paste prompts
- [Templates Directory](templates/) - Starter files

### External Resources
- [MCP Protocol Specification](https://modelcontextprotocol.io/)
- [Claude Desktop Download](https://claude.ai/download)
- [FastMCP Documentation](https://github.com/jlowin/fastmcp)

## 🗺️ Roadmap

### Current (v1.0)
- ✅ Complete system instructions
- ✅ Agent-centric design patterns
- ✅ Test-driven workflow
- ✅ FastMCP-first approach
- ✅ Token optimization patterns (optional)
- ✅ Token transparency for workflow servers
- ✅ Comprehensive documentation

### Future (TBD)

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built on patterns from multiple MCP servers
- Inspired by real-world token optimization challenges (99% reduction achieved)
- Powered by Claude and FastMCP
- Thanks to the Model Context Protocol community
- Thanks to all contributors and early adopters

## 🌟 Success Stories

This system instruction approach has been used to build:
- **Pipeline Health Monitor** - 98.9% token reduction (37,795 → 421 tokens per check)
- **Multi-service orchestrators** - 5 APIs, 1 tool call
- **Data platform explorers** - Complete data platform visibility in 1-2 calls

## ⭐ Show Your Support

If this project helped you build better MCP servers, give it a star! ⭐

It helps others discover these patterns and encourages continued development.

---

**Ready to build?** Start with the [Quick Start Guide](QUICKSTART.md) →

**Questions?** Check the [Documentation](docs/)