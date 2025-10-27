# MCP Server Development Request Template

Choose the appropriate workflow template based on your goal:

---

## 🎯 Workflow 1: Integrate Managed MCP Server (e.g., Snowflake)

**Use this when:** A vendor provides an official MCP server that you want to add to Claude Desktop.

### Request Format:

```
I want to integrate the [SERVICE NAME] managed MCP server into my Claude Desktop.

**Service Details:**
- Service: [e.g., Snowflake, GitHub, PostgreSQL]
- Documentation URL: [link to MCP server docs]
- Server Type: [npx package, Python package, or standalone]

**My Environment:**
- Operating System: [macOS, Windows, Linux]
- Python Version: [if applicable]
- Node.js Version: [if applicable]
- Installation Preference: [local project, global npm, etc.]
- IDE:[VSCode, Cursor, etc.]

**Authentication:**
- Auth Method: [API Key, OAuth, Username/Password, PAT]
- I have credentials: [Yes/No - don't share actual credentials yet]

**What I Want to Do:**
[Describe the operations you want to perform with this service]

**Current Setup:**
- My existing MCP servers: [list them, e.g., "Service_Name MCP server"]
- My config file location: [show path to claude_desktop_config.json]
```

### Example (Snowflake):

```
I want to integrate Snowflake database access into my Claude Desktop.

**Service Details:**
- Service: Snowflake
- Approach: Build a custom Python MCP server
- Documentation: https://docs.snowflake.com/

**My Environment:**
- Operating System: [macOS, Windows, Linux]
- Python Version: [if applicable]
- Node.js Version: [if applicable]
- Installation Preference: [local project, global npm, etc.]
- IDE:[VSCode, Cursor, etc.]

**Authentication:**
- Auth Method: [API Key, OAuth, Username/Password, PAT]
- I have credentials: [Yes/No - don't share actual credentials yet]

**What I Want to Do:**
- Query Snowflake tables using natural language
- Check data freshness and row counts
- Execute custom SQL queries
- Eventually orchestrate with my service_name MCP server for data quality workflows

**Current Setup:**
- My existing MCP servers: My current MCP Servers
- My config file location: ~/Library/Application Support/Claude/claude_desktop_config.json
- Projects location: ~/folder/GitHub/
```

---

## 🛠️ Workflow 2: Build Custom MCP Server from Scratch

**Use this when:** You need to integrate with an API/service that doesn't have an existing MCP server.

### Request Format:

```
I want to build a custom MCP server for [SERVICE NAME].

**Service Details:**
- Service Name: [e.g., Stripe, Internal API, Custom Database]
- API Documentation: [link if available]
- Authentication Type: [API Key, OAuth, Basic Auth, etc.]
- Base URL: [API endpoint base]

**Operations Needed:**
List the specific operations you want to perform:
1. [e.g., List all customers]
2. [e.g., Create new invoice]
3. [e.g., Get payment status]
4. [etc.]

**My Environment:**
- Operating System: [macOS, Windows, Linux]
- Preferred Language: [Python or Node.js]
- Development Tools: [VS Code, Cursor, etc.]
- Python/Node Version: [version number]

**My Experience Level:**
- [Beginner / Intermediate / Advanced] with Python/Node.js
- [Beginner / Intermediate / Advanced] with APIs
- [First time / Experienced] building MCP servers

**Project Setup:**
- Where I store projects: [e.g., ~/folder/GitHub/]
- Naming preference: [e.g., service-name-mcp-server]

**Reference:**
My existing MCP servers which are attached as files to the system instructions: MCP Server Name 1, 2, 3, etc.
```

### Example (Stripe):

```
I want to build a custom MCP server for Stripe.

**Service Details:**
- Service Name: Stripe
- API Documentation: https://stripe.com/docs/api
- Authentication Type: API Key (Secret Key)
- Base URL: https://api.stripe.com

**Operations Needed:**
1. List all customers
2. Get customer details by ID
3. Create new customer
4. List recent charges
5. Get payment intent status
6. Create invoice
7. List subscriptions

**My Environment:**
- Operating System: [macOS, Windows, Linux]
- Preferred Language: [Python or Node.js]
- Development Tools: [VS Code, Cursor, etc.]
- Python/Node Version: [version number]

**My Experience Level:**
- [Beginner / Intermediate / Advanced] with Python/Node.js
- [Beginner / Intermediate / Advanced] with APIs
- [First time / Experienced] building MCP servers

**Project Setup:**
- Where I store projects: ~/folder/GitHub/
- Naming preference: stripe-mcp-server

**Reference:**
I have a Service_Name MCP server working as a reference implementation.
```

---

## 🔄 Workflow 3: Two-Server Orchestration Setup

**Use this when:** You have two working MCP servers and want to create workflows that use both.

### Request Format:

```
I want to set up orchestration between my [SERVER 1] and [SERVER 2] MCP servers.

**Current Servers:**
- Server 1: [name] - Status: [Working / Needs fixes]
- Server 2: [name] - Status: [Working / Needs fixes]

**Orchestration Goal:**
[Describe the high-level workflow you want to achieve]

**Specific Use Cases:**
1. **Use Case 1 Name**: [Brief description]
   - Expected workflow: [Step by step what should happen]
   - Example command: "[Natural language command to trigger this]"

2. **Use Case 2 Name**: [Brief description]
   - Expected workflow: [Step by step]
   - Example command: "[Natural language command]"

**Questions:**
- Do both servers need updates to work together? [Yes/No/Not sure]
- Are there specific tool improvements needed? [Describe if any]
- Do you need help testing the orchestration? [Yes/No]
```

### Example (Fivetran + Snowflake):

```
I want to set up orchestration between my Fivetran and Snowflake MCP servers.

**Current Servers:**
- Server 1: Fivetran MCP Server - Status: Working
- Server 2: Snowflake MCP Server - Status: Needs to be installed and configured

**Orchestration Goal:**
Enable end-to-end data pipeline monitoring and management without leaving Claude Desktop. Never need to open Fivetran or Snowflake UIs.

**Specific Use Cases:**

1. **Data Quality Check**: 
   - Expected workflow:
     1. Check Fivetran sync status for Salesforce connection
     2. Get last sync time and row counts from Fivetran
     3. Query Snowflake for Salesforce table row counts
     4. Compare Fivetran metrics with Snowflake data
     5. Alert if discrepancies found
   - Example command: "What's my data quality looking like for Salesforce?"

2. **New Source Onboarding**:
   - Expected workflow:
     1. Monitor Fivetran PostgreSQL connection sync status
     2. Wait for initial sync completion
     3. Query Snowflake to inspect new table schemas
     4. Create Snowflake view joining new data with existing tables
     5. Confirm view creation and show sample results
   - Example command: "We just connected PostgreSQL in Fivetran. Once sync completes, create a view joining it with customer data."

3. **Performance Troubleshooting**:
   - Expected workflow:
     1. Check all Fivetran connection sync statuses
     2. Identify any delays or paused connections
     3. Query Snowflake for table last update times
     4. Check Snowflake for long-running queries
     5. Synthesize findings with specific recommendations
   - Example command: "Our dashboard shows stale data. Figure out where the bottleneck is."

4. **Cost Optimization**:
   - Expected workflow:
     1. List all Fivetran connectors with sync frequencies
     2. Query Snowflake usage views for data ingestion by schema
     3. Check Snowflake warehouse credit consumption during sync times
     4. Provide actionable recommendations
   - Example command: "Which Fivetran connectors sync the most data and how much Snowflake compute do they use?"

**Questions:**
- Do both servers need updates to work together? Not sure - Snowflake server isn't set up yet
- Are there specific tool improvements needed? Maybe - need to evaluate once Snowflake is working
- Do you need help testing the orchestration? Yes, definitely want to test each use case
```

---

## 🌐 Workflow 4: Multi-Server Ecosystem (3+ Servers)

**Use this when:** You want to orchestrate three or more MCP servers together.

### Request Format:

```
I want to build a multi-server ecosystem with [NUMBER] MCP servers.

**Servers to Include:**
1. [Server 1 name] - Status: [Working/Not started/In progress]
2. [Server 2 name] - Status: [Working/Not started/In progress]
3. [Server 3 name] - Status: [Working/Not started/In progress]
[Add more as needed]

**Ecosystem Goal:**
[Describe the comprehensive workflow/capability you want]

**Complex Use Cases:**
[Describe 2-3 advanced workflows that require all servers]

**Priority:**
Which servers/use cases should we tackle first?
1. [First priority]
2. [Second priority]
3. [Third priority]
```

### Example (Fivetran + Snowflake + dbt + Slack):

```
I want to build a multi-server ecosystem with 4 MCP servers.

**Servers to Include:**
1. Fivetran MCP Server - Status: Working (53 tools)
2. Snowflake MCP Server - Status: Not started (next priority)
3. dbt MCP Server - Status: Not started
4. Slack MCP Server - Status: Not started

**Ecosystem Goal:**
Complete data stack automation - from ingestion through transformation to monitoring and alerting, all through natural language commands in Claude Desktop.

**Complex Use Cases:**

1. **Automated Data Pipeline Deployment**:
   - Deploy new dbt models to production
   - Trigger Fivetran schema refresh for affected sources
   - Wait for sync completion
   - Run dbt transformation
   - Validate results in Snowflake
   - Post success/failure to Slack channel

2. **Proactive Issue Detection**:
   - Monitor Fivetran sync health every hour
   - Check Snowflake query performance
   - Identify dbt models with long run times
   - Alert team in Slack if issues detected
   - Provide diagnostic details and suggested fixes

3. **End-to-End Impact Analysis**:
   - "What happens if I pause the Salesforce connector?"
   - Show affected Snowflake tables
   - Identify dependent dbt models
   - List downstream dashboards/reports
   - Estimate data freshness impact

**Priority:**
1. Get Snowflake MCP server working first
2. Build Fivetran + Snowflake orchestration (prove the concept)
3. Add dbt server and 3-way orchestration
4. Add Slack for notifications (enhancement)
```

---

## 🔧 Workflow 5: Troubleshooting Existing MCP Server

**Use this when:** You have an MCP server that's not working correctly.

### Request Format:

```
I need help troubleshooting my [SERVER NAME] MCP server.

**Problem Description:**
[Clearly describe what's not working]

**Server Details:**
- Server Name: [name]
- Language: [Python/Node.js]
- Location: [full path]
- Config Entry: [paste your claude_desktop_config.json entry for this server]

**What I've Tried:**
1. [Step 1]
2. [Step 2]
[etc.]

**Error Messages:**
```
[Paste any error messages here]
```

**Logs:**
```
[Paste relevant log output if available]
```

**Environment:**
- Operating System: [macOS/Windows/Linux]
- Claude Desktop Version: [if known]
- Python/Node Version: [version]

**Testing Results:**
- Does server start manually? [Yes/No - explain]
- Are dependencies installed? [Yes/No]
- Do credentials work outside MCP? [Yes/No]
```

---

## 📋 Quick Reference: When to Use Each Workflow

| Goal | Workflow | Time Estimate |
|------|----------|---------------|
| Add Snowflake/GitHub/etc official MCP server | Workflow 1 | 15-30 min |
| Build custom server (Stripe, internal API) | Workflow 2 | 2-4 hours |
| Connect 2 working servers | Workflow 3 | 1-2 hours |
| Build comprehensive ecosystem (3+ servers) | Workflow 4 | Multiple days |
| Fix broken server | Workflow 5 | 30 min - 2 hours |

---

## 🎯 What to Include in Your Request

**Always Include:**
- ✅ Clear goal statement
- ✅ Your operating system
- ✅ Current working servers (if any)
- ✅ Specific use cases or operations needed

**Include When Relevant:**
- ✅ API documentation links
- ✅ Authentication details (type, not actual credentials)
- ✅ Error messages or logs
- ✅ Your experience level
- ✅ Timeline or urgency

**Never Include:**
- ❌ Actual API keys, passwords, or tokens
- ❌ Company-sensitive information
- ❌ Personal data

---

## 💡 Tips for Best Results

1. **Start with one workflow** - Don't try to do everything at once
2. **Test incrementally** - Validate each stage before moving forward
3. **Use the reference** - Fivetran MCP server is your blueprint
4. **Be specific** - The more detail you provide, the better the guidance
5. **Ask questions** - If you're unsure about something, ask before proceeding

---