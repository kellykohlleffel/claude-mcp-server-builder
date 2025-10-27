# MCP Server Development Project - Complete Setup Guide

## 📁 Project Structure

This Claude Project enables you to develop, integrate, and orchestrate MCP servers for Claude Desktop. Here's how to set it up for maximum effectiveness.

---

## 🎯 Project Configuration

### Project Name
**"MCP Server Development & Integration"**

### Project Description
```
Expert assistance for building, configuring, and orchestrating Model Context Protocol (MCP) servers for Claude Desktop. Specializes in Python and Node.js MCP implementations, multi-server orchestration, and natural language data stack automation.
```

---

## 📎 Required Attachments

### System Prompt Attachments

These provide Claude with deep context about MCP server development. If you want to use the Fivetran example below, you can access a [Fivetran MCP toolkit here](https://github.com/kellykohlleffel/fivetran-mcp-toolkit).

#### 1. **Fivetran MCP Server README** (CRITICAL)
- **File**: `README.md` from the Fivetran MCP Toolkit repo
- **Purpose**: Reference implementation showing best practices
- **Why**: Provides working examples of multiple tools, error handling, multi-account management, and documentation patterns

#### 2. **MCP Protocol Specification** (Recommended)
- **Source**: https://modelcontextprotocol.io/
- **What to attach**: Copy key sections into a markdown file:
  - Protocol overview
  - Transport layers (stdio)
  - Resource/Tool/Prompt schemas
  - Error handling patterns
- **Purpose**: Ensures technical accuracy

#### 3. **Fivetran MCP Server Source Code** (Recommended from the repo referenced above)
- **Files to attach**:
  - `fivetran_mcp_server.py` - Shows tool structure
  - `fivetran_client.py` - Shows API client patterns
  - `run_server.py` - Shows entry point pattern
- **Purpose**: Concrete code examples for reference

#### 4. **Your claude_desktop_config.json** (Sanitized)
- **File**: Your current config with secrets removed
- **Purpose**: Shows your current setup, paths, and structure
- **How to view/edit**:
```bash
# View in terminal
cat ~/Library/Application\ Support/Claude/claude_desktop_config.json

# Edit in VS Code
code ~/Library/Application\ Support/Claude/claude_desktop_config.json
```
- **How to sanitize**:
```json
{
  "mcpServers": {
    "fivetran": {
      "command": "/Users/USERNAME/yourfolder1/GitHub/fivetran-mcp-server/mcpvenv/bin/python",
      "args": ["/Users/USERNAME/yourfolder1/GitHub/fivetran-mcp-server/run_server.py"],
      "cwd": "/Users/USERNAME/yourfolder1/GitHub/fivetran-mcp-server",
      "env": {
        "FIVETRAN_API_KEY": "REDACTED",
        "FIVETRAN_API_SECRET": "REDACTED"
      }
    }
  }
}
```

---

### User Prompt Attachments (Optional but Helpful)

These are documents you might attach when making specific requests:

#### For New Server Development:
- **API Documentation** - Link or PDF of the service's API docs
- **Authentication Guide** - How the API handles auth
- **Example API Responses** - Sample JSON responses (sanitized)

#### For Troubleshooting:
- **Error Logs** - Recent error messages from server or Claude Desktop
- **Server Code** - The specific file that's causing issues
- **Requirements File** - `requirements.txt` or `package.json`

#### For Orchestration:
- **Use Case Diagrams** - Visual workflow of what you want to achieve
- **Current Server List** - Summary of all working MCP servers
- **Example Commands** - Natural language commands you want to enable

---

## 🚀 Step-by-Step Setup

### Step 1: Create the Claude Project

1. **Open Claude Desktop**
2. **Click "Projects" in the left sidebar**
3. **Click "+ New Project"**
4. **Name it**: "MCP Server Development & Integration"
5. **Add description** (copy from above)

### Step 2: Add System Instructions

1. **In your new project, click "Edit Project"**
2. **Paste the System Instructions** from the `MCP System Prompt` artifact here in the docs folder
3. **Save**

### Step 3: Attach System Prompt Documents

1. **Still in "Edit Project" mode**
2. **Click "Files" under Project Knowledge**
3. **Add these files** (in order of priority):

**Essential (Start with these):**
- ✅ Fivetran MCP Server README.md
- ✅ Your sanitized claude_desktop_config.json

**Highly Recommended (Add when ready):**
- ✅ Fivetran MCP Server source code files
- ✅ MCP Protocol docs (create markdown summary)

**Optional (Add as needed):**
- Any other working MCP servers you have
- Custom documentation you've written
- Troubleshooting notes

### Step 4: Test the Project

Start a new conversation in your project and test:

```
I'm ready to work on MCP servers. Can you:
1. Confirm you have access to my Fivetran MCP server documentation
2. Tell me what you know about my current setup
3. Explain how you can help me add the Snowflake MCP server (or whatever MCP Server you want to build)
```

You should get a response that references your Fivetran setup specifically.

---

## 📋 Using the Project

### For Each New Task

1. **Start with the User Prompt Template**
   - Copy the appropriate workflow template
   - Fill in your specific details
   - Paste into a new conversation in the project

2. **Attach Relevant Documents**
   - API docs for new integrations
   - Error logs for troubleshooting
   - Existing code for extensions

3. **Follow the Guidance**
   - Claude will provide step-by-step instructions
   - Test each stage before proceeding
   - Ask clarifying questions as needed

### Typical Conversation Flow

**You**: [Use Workflow 1 template to request Snowflake MCP integration]

**Claude**: 
- Asks clarifying questions
- Provides installation commands
- Gives you the claude_desktop_config.json entry
- Explains how to test

**You**: [Follow instructions, report results]

**Claude**:
- Helps troubleshoot if needed
- Provides next steps
- Documents the working solution

---

## 🎯 Progressive Development Path

### Phase 1: Foundation (Week 1)
- ✅ **Done**: Fivetran MCP Server working (start with a few tools and work your way up)
- 🎯 **Next**: Add Snowflake MCP Server
- 🎯 **Validate**: Both servers work independently

### Phase 2: Two-Server Orchestration (Week 2)
- 🎯 Build use case: Data quality check
- 🎯 Build use case: Performance troubleshooting
- 🎯 Build use case: Cost optimization
- 🎯 Document patterns that emerge

### Phase 3: Expand Ecosystem (Week 3-4)
- 🎯 Add dbt MCP Server
- 🎯 Add Slack MCP Server (optional)
- 🎯 Build 3 or 4-way workflows
- 🎯 Create automation patterns

### Phase 4: Production Hardening (Ongoing)
- 🎯 Add error handling and retries
- 🎯 Implement rate limiting
- 🎯 Add monitoring and logging
- 🎯 Document all workflows

---

## 🔍 Quick Reference Commands

### Check Project Status
```
What MCP servers do I currently have working?
List all the capabilities I have available.
```

### Start New Server Integration
```
[Use Workflow 1 or 2 template from User Prompt Template artifact]
```

### Troubleshoot Issues
```
[Use Workflow 5 template from User Prompt Template artifact]
```

### Plan Orchestration
```
I have [Server A] and [Server B] working. How should I approach building orchestration between them for [specific use case]?
```

---

## 📊 Success Metrics

Track your progress:

| Metric | Target | Current |
|--------|--------|---------|
| Working MCP Servers | 3-5 | 1 (Fivetran) |
| Two-Server Workflows | 4-6 | 0 |
| Complex Orchestrations | 2-3 | 0 |
| Daily Use Cases | 10+ | TBD |

---

## 💡 Best Practices

### Do's ✅
- Start with one server at a time with limited tools (the simplest approach is to start with an API that doesn't require any authentication - there are many of these available, just pick one that interests you)
- Test thoroughly before adding complexity
- Document working configurations immediately
- Use the Fivetran server as your reference
- Ask questions when unsure
- Keep credentials secure (never in project attachments)

### Don'ts ❌
- Don't try to build everything at once
- Don't skip testing phases
- Don't commit credentials to git
- Don't use relative paths in configs
- Don't assume – verify each step
- Don't move on until current step works

---

## 🆘 Troubleshooting

### "Claude doesn't seem to know about my Fivetran server"
- **Fix**: Ensure Fivetran README is attached to project
- **Check**: Look in Project Knowledge section
- **Test**: Ask "What do you know about my Fivetran setup?"

### "Getting generic responses, not specific to my setup"
- **Fix**: Attach your sanitized claude_desktop_config.json
- **Fix**: Include more context in your request
- **Fix**: Reference specific files/configurations

### "Suggested code doesn't match my environment"
- **Fix**: Specify your OS, Python version, paths in request
- **Fix**: Include your current working directory structure
- **Fix**: Show example of working code from Fivetran server

---

## 📚 Additional Resources

### Official Documentation
- [MCP Protocol Spec](https://modelcontextprotocol.io/)
- [Claude Desktop Download](https://claude.ai/download)
- [Fivetran API Docs](https://fivetran.com/docs/rest-api)
- [Snowflake MCP Docs](https://docs.snowflake.com/en/user-guide/snowflake-cortex/cortex-agents-mcp)

### Your Repositories
- [Fivetran MCP Toolkit](https://github.com/kellykohlleffel/fivetran-mcp-toolkit)
- Future: Snowflake MCP Server
- Future: dbt MCP Server

---

## 🎓 Learning Path

### Beginner → Intermediate
1. ✅ Get one MCP server working (Fivetran - done!)
2. 🎯 Add second managed server (Snowflake)
3. 🎯 Build simple orchestration (2 tools working together)
4. 🎯 Handle errors gracefully

### Intermediate → Advanced
1. 🎯 Build custom MCP server from scratch
2. 🎯 Implement complex 3+ server workflows
3. 🎯 Add monitoring and alerting
4. 🎯 Optimize for production use

### Advanced → Expert
1. 🎯 Create reusable MCP server templates
2. 🎯 Build server management tools
3. 🎯 Contribute to MCP ecosystem
4. 🎯 Share patterns with community

---

## ✅ Next Steps

**Immediate (Today):**
1. Set up this Claude Project with system instructions
2. Attach Fivetran README and sanitized config
3. Test with a simple query about your setup

**This Week:**
1. Use Workflow 1 to integrate Snowflake MCP Server
2. Test Snowflake independently
3. Build first Fivetran + Snowflake orchestration

**This Month:**
1. Create 4-6 two-server workflows
2. Document patterns that emerge
3. Plan third server integration (dbt or other)

**This Quarter:**
1. Build comprehensive multi-server ecosystem
2. Automate common workflows
3. Eliminate manual UI usage for routine tasks

---

## 🎉 You're Ready!

Your MCP Server Development Project is now set up to be a powerful tool for building and orchestrating your data stack through natural language commands.

Remember:
- **Start simple** - One server at a time
- **Test thoroughly** - Validate before adding complexity  
- **Use your reference** - Fivetran server shows the way
- **Ask questions** - Better to clarify than assume
- **Document wins** - Save working configurations immediately

**Let's build something amazing! 🚀**