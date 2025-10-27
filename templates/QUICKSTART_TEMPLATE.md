# [Your Service] MCP Server - Quick Start

> Quick setup guide for the [Your Service] MCP server

## Prerequisites

- Python 3.10 or higher
- [Your Service] account with API access
- [Your Service] API credentials ([link to how to get them])

## Quick Setup

### 1. Clone or Create Project

```bash
mkdir ~/Documents/GitHub/your-service-mcp-server
cd ~/Documents/GitHub/your-service-mcp-server
```

### 2. Create Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment

```bash
# Copy the environment template
cp .env.example .env

# Edit .env with your credentials
# [EDITOR] .env
```

Add your credentials:
```env
API_KEY=your_api_key_here
API_SECRET=your_api_secret_here  # if applicable
```

### 5. Test API Connection

```bash
python test_client.py
```

Expected output:
```
============================================================
Testing Authentication
============================================================
✅ API_KEY configured
✅ Connected to [Your Service] API

============================================================
Testing Core Operations
============================================================
✅ List resources: 5 items found
✅ Get resource details: Success
✅ Search resources: 3 results found

============================================================
Test Summary
============================================================
✅ Passed: 5
❌ Failed: 0

🎉 All tests passed! Ready for MCP server.
```

### 6. Test MCP Tools Locally

```bash
python test_server.py
```

Expected output:
```
============================================================
Testing MCP Tools
============================================================
✅ Health check passed
✅ List items tool working
✅ Get item tool working
✅ Search tool working
✅ Error handling working

============================================================
Test Summary
============================================================
✅ Passed: 5
❌ Failed: 0

🎉 All tools working! Ready for Claude Desktop.
```

### 7. Configure Claude Desktop

Get your system paths:
```bash
whoami              # Your username
pwd                 # Current directory
which python        # Python executable path (with venv activated)
```

Edit Claude Desktop config:
```bash
# macOS/Linux
code ~/Library/Application\ Support/Claude/claude_desktop_config.json

# Or manually edit the file
```

Add this configuration (replace paths with yours):
```json
{
  "mcpServers": {
    "your-service": {
      "command": "/Users/YOUR_USERNAME/Documents/GitHub/your-service-mcp-server/venv/bin/python",
      "args": ["/Users/YOUR_USERNAME/Documents/GitHub/your-service-mcp-server/run_server.py"],
      "cwd": "/Users/YOUR_USERNAME/Documents/GitHub/your-service-mcp-server",
      "env": {
        "API_KEY": "your_api_key_here",
        "API_SECRET": "your_api_secret_here"
      }
    }
  }
}
```

**⚠️ Important:** Use absolute paths (not `~`)

### 8. Restart Claude Desktop

1. **Completely quit** Claude Desktop (Cmd+Q on Mac, not just close window)
2. Wait 5 seconds
3. Reopen Claude Desktop
4. Start a **new conversation**
5. Check Settings → Developer to verify server is connected

### 9. Test Integration

Try these commands in Claude:

```
# Health check
Check [Your Service] connection

# List resources
List my [resources] from [Your Service]

# Get details
Get details for [resource_name]

# Search
Search [Your Service] for [query]
```

---

## Available Tools

This MCP server provides the following tools:

### Core Operations
- `your_service_health_check` - Test API connectivity
- `your_service_list_items` - List all available resources
- `your_service_get_item` - Get details for a specific resource
- `your_service_search` - Search resources by query
- `your_service_get_stats` - Get usage statistics

### Additional Operations
- [Add your additional tools here]

---

## Project Structure

```
your-service-mcp-server/
├── venv/                      # Virtual environment
├── .env                       # Your credentials (DO NOT COMMIT)
├── .env.example              # Environment template
├── .gitignore                # Git ignore rules
├── requirements.txt          # Python dependencies
├── QUICKSTART.md             # This file
├── test_client.py            # API client tests
├── test_server.py            # MCP tool tests
├── your_service_client.py    # API client wrapper
├── your_service_mcp_server.py # MCP server implementation
└── run_server.py             # Entry point
```

---

## Troubleshooting

### "Connection failed" in test_client.py
- ✅ Check API_KEY is set in .env
- ✅ Verify credentials are valid
- ✅ Check network connectivity
- ✅ Review API documentation for changes

### "Server won't start" in Claude Desktop
- ✅ Verify absolute paths in config (no `~`)
- ✅ Check Python path is correct: `which python` (with venv activated)
- ✅ Ensure working directory (cwd) is correct
- ✅ Validate JSON syntax: `python -m json.tool config.json`

### "Tools not showing up" in Claude
- ✅ Restart Claude Desktop completely (Cmd+Q)
- ✅ Start a NEW conversation (old ones don't see new servers)
- ✅ Check Settings → Developer for server status
- ✅ Review logs: `~/Library/Logs/Claude/mcp*.log`

### "Tools fail when called"
- ✅ Verify test_client.py passed all tests
- ✅ Verify test_server.py passed all tests
- ✅ Check credentials in Claude Desktop config env section
- ✅ Review server logs for specific errors

---

## Development Workflow

### Making Changes

1. **Modify code**
   ```bash
   # Edit your server files
   code your_service_mcp_server.py
   ```

2. **Test locally first**
   ```bash
   python test_server.py
   ```

3. **Only after tests pass, restart Claude Desktop**
   ```bash
   # Cmd+Q to quit
   # Wait 5 seconds
   # Reopen
   ```

### Adding New Tools

1. Add function to `your_service_client.py`
2. Test in `test_client.py`
3. Add MCP tool to `your_service_mcp_server.py`
4. Test in `test_server.py`
5. Restart Claude Desktop
6. Test in Claude

---

## Configuration Reference

### Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `API_KEY` | Yes | Your [Service] API key |
| `API_SECRET` | Maybe | Your [Service] API secret (if applicable) |
| `API_BASE_URL` | No | Override default API URL |
| `LOG_LEVEL` | No | Logging level (default: INFO) |

### Rate Limits

[Document your API's rate limits]
- Requests per second: X
- Requests per hour: Y
- Concurrent requests: Z

---

## Support

- **Documentation**: [Link to your service's API docs]
- **Issues**: [Link to your GitHub issues]
- **Questions**: [Link to discussions or support channel]

---

## Next Steps

- [ ] Test all core operations work
- [ ] Add any custom tools you need
- [ ] Test error handling
- [ ] Document your specific workflows
- [ ] Share with your team

---

## Credits

Built using [Claude MCP Server Builder](https://github.com/YOUR_USERNAME/claude-mcp-server-builder)
