# MCP Server Builder - Quick Start Guide

Get your Claude Project set up and start building MCP servers in 5 minutes.

## 🎯 What You'll Build

Use this system to:
- Build custom MCP servers for any API or service
- Integrate vendor-provided managed MCP servers
- Test servers systematically before Claude Desktop integration
- Create multi-server orchestrations through natural language

**Time to first working server:** 2-4 hours

---

## 🚀 Quick Start (5 Minutes)

### Step 1: Create Claude Project (2 min)

1. Open [Claude.ai](https://claude.ai)
2. Click **"Projects"** → **"Create Project"**
3. Name it: **"MCP Server Builder"** (or your preference)

### Step 2: Add System Instructions (2 min)

1. In your project, click **"Project Settings"**
2. Go to **"Custom Instructions"**
3. Copy the entire contents of [`docs/SYSTEM_INSTRUCTIONS.md`](docs/SYSTEM_INSTRUCTIONS.md)
4. Paste into Custom Instructions field
5. Click **"Save"**

### Step 3: Start Building (1 min)

Use this starter prompt:

```
I want to build an MCP server for [SERVICE_NAME] that integrates with Claude Desktop.

Service details:
- Type: [REST API / Database / SaaS Platform]
- Authentication: [API key / OAuth / Database credentials]
- Key operations I need:
  1. [Operation 1]
  2. [Operation 2]
  3. [Operation 3]

Let's start with creating test_client.py to validate the API works.
```

**That's it!** Claude will guide you through the rest.

---

## 📋 What Happens Next

Claude will guide you through this workflow:

1. **✅ Create test_client.py** - Test API authentication and operations
2. **✅ Build API client** - Create the service client wrapper
3. **✅ Build MCP server** - Implement MCP tools using FastMCP
4. **✅ Create test_server.py** - Test MCP tools locally
5. **✅ Configure Claude Desktop** - Add server to your config
6. **✅ Integration testing** - Verify everything works

**Testing Flow:**
```
test_client.py ✅ → Build Server → test_server.py ✅ → Claude Desktop ✅
```

---

## 🎓 Your First Server

### Example: Building a Weather API MCP Server

**Step 1: Start the conversation**
```
I want to build an MCP server for OpenWeatherMap API.

Service details:
- Type: REST API
- Base URL: https://api.openweathermap.org/data/2.5
- Authentication: API key (I have one)
- Key operations:
  1. Get current weather for a city
  2. Get 5-day forecast
  3. Search cities

Let's start with test_client.py.
```

**Step 2: Follow Claude's guidance**
- Claude creates test_client.py with your API
- You run it: `python test_client.py`
- If tests pass ✅, proceed to build MCP server
- If tests fail ❌, debug API issues first

**Step 3: Build the MCP server**
- Claude generates the MCP server code using FastMCP
- Creates test_server.py for local testing
- You test: `python test_server.py`

**Step 4: Configure Claude Desktop**
- Claude provides exact config for your system
- You add to `~/Library/Application Support/Claude/claude_desktop_config.json`
- Restart Claude Desktop
- Test with: "What's the weather in San Francisco?"

---

## 💡 Common Use Cases

### REST API Integration
- Payment APIs (Stripe, PayPal)
- Communication APIs (Twilio, SendGrid)
- Project management (Jira, Linear)
- Custom internal APIs

### Database Integration
- PostgreSQL
- MySQL
- Snowflake
- BigQuery

### SaaS Platform Integration
- GitHub
- Slack
- Notion
- Custom tools

---

## 📚 Full Documentation

For detailed information:

- **[docs/SYSTEM_INSTRUCTIONS.md](docs/SYSTEM_INSTRUCTIONS.md)** - Complete system prompt
- **[docs/USER_PROMPT_TEMPLATE.md](docs/USER_PROMPT_TEMPLATE.md)** - Prompt templates for different scenarios
- **[docs/PROJECT_SETUP.md](docs/PROJECT_SETUP.md)** - Detailed project configuration guide

---

## 🐛 Troubleshooting

### "Claude doesn't seem to know about MCP servers"
- **Check:** Are you in the MCP Server Builder project?
- **Fix:** Look for the project name at the top of the conversation
- **Fix:** Make sure you added the system instructions

### "Server won't start in Claude Desktop"
- **Fix:** Verify you're using absolute paths (not `~`)
- **Fix:** Check that Python virtual environment is activated
- **Fix:** Run `python test_server.py` first to validate locally

### "Tools not working"
- **Check:** Did `test_client.py` pass all tests?
- **Check:** Did `test_server.py` pass all tests?
- **Fix:** Debug in that order - API first, then tools

---

## ✅ Success Checklist

You're ready when:
- [ ] Claude Project created with system instructions
- [ ] You have API credentials for the service you want to integrate
- [ ] You understand the basic workflow (test → build → test → integrate)

---

## 🎯 What Makes This System Special

**Test-Driven:** Never build MCP server before validating API works

**FastMCP-First:** Use the fastest path to working servers (90% of cases)

**Flat Structure:** Simple project layout - no nested folders to manage

**Local Testing:** Test tools without Claude Desktop restarts

**Production Patterns:** Based on real servers with 50+ tools in production

---

## 🚀 Ready to Build?

1. ✅ Create your Claude Project (2 minutes)
2. ✅ Add system instructions (2 minutes)  
3. ✅ Use the starter prompt above (1 minute)
4. 🎉 Start building your first MCP server!

**Questions?** Just ask in your project - that's what it's built for!

---

## 📖 Next Steps

After your first server works:

1. **Add a second server** - Try a different API or database
2. **Learn orchestration** - Use multiple servers together
3. **Read the patterns** - See [examples/](examples/) for reference implementations
4. **Share your learnings** - Contribute patterns back to the community

**Let's build something amazing! 🚀**
