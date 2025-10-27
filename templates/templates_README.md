# Templates Directory

This directory contains starter templates for building MCP servers. Copy these files to your MCP server project and customize them.

## 📋 Files Included

### `.env.example`
**Purpose:** Environment variables template for API credentials and configuration

**Usage:**
```bash
cp .env.example .env
# Edit .env with your actual credentials
```

**Contains:**
- API authentication templates
- Database connection strings
- Rate limiting configuration
- Logging settings
- Feature flags

**⚠️ Security:** Never commit the actual `.env` file to git!

---

### `.gitignore`
**Purpose:** Comprehensive gitignore for Python MCP projects

**Usage:**
```bash
cp .gitignore /your-mcp-project/.gitignore
```

**Includes:**
- Environment files (`.env`, credentials)
- Python artifacts (`__pycache__`, `*.pyc`)
- Virtual environments (`venv/`, `.venv/`)
- IDE files (`.vscode/`, `.idea/`)
- OS files (`.DS_Store`, `Thumbs.db`)
- Test outputs and logs

---

### `requirements.txt`
**Purpose:** Common Python dependencies for MCP servers

**Usage:**
```bash
cp requirements.txt /your-mcp-project/
pip install -r requirements.txt
```

**Includes:**
- FastMCP (recommended framework)
- python-dotenv (environment management)
- requests/httpx (HTTP clients)
- Testing frameworks (pytest)
- Code quality tools (black, ruff, mypy)
- Common optional dependencies (commented out)

**Customize:** Uncomment and add dependencies specific to your service

---

### `QUICKSTART_TEMPLATE.md`
**Purpose:** Template for your MCP server's quickstart guide

**Usage:**
```bash
cp QUICKSTART_TEMPLATE.md /your-mcp-project/QUICKSTART.md
# Replace placeholders with your service name and specifics
```

**Replace:**
- `[Your Service]` → Your actual service name
- `your-service` → Your project name (lowercase-hyphenated)
- API endpoints and examples
- Tool names and descriptions

**Keep:**
- The overall structure and workflow
- Testing approach
- Troubleshooting sections

---

## 🚀 Quick Start for New Project

### 1. Create Project Directory
```bash
mkdir ~/Documents/GitHub/my-service-mcp-server
cd ~/Documents/GitHub/my-service-mcp-server
```

### 2. Copy Templates
```bash
# Copy all templates
cp /path/to/claude-mcp-server-builder/templates/.env.example .
cp /path/to/claude-mcp-server-builder/templates/.gitignore .
cp /path/to/claude-mcp-server-builder/templates/requirements.txt .
cp /path/to/claude-mcp-server-builder/templates/QUICKSTART_TEMPLATE.md QUICKSTART.md
```

### 3. Set Up Environment
```bash
# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env with your credentials
```

### 4. Build Your Server
Use the [User Prompt Template](../docs/USER_PROMPT_TEMPLATE.md) to guide Claude through building your server.

---

## 📝 Customization Guide

### For REST API Services
1. Keep `.env.example` API_KEY section
2. Add service-specific environment variables
3. Uncomment `requests` or `httpx` in `requirements.txt`
4. Update QUICKSTART with your API endpoints

### For Database Services
1. Add database connection string to `.env.example`
2. Uncomment database adapter in `requirements.txt` (e.g., `psycopg2-binary` for PostgreSQL)
3. Update QUICKSTART with database setup instructions
4. Add database-specific troubleshooting

### For OAuth Services
1. Add OAuth tokens and refresh tokens to `.env.example`
2. Uncomment `oauthlib` in `requirements.txt`
3. Note: OAuth may not work with Claude Desktop (consider building custom with PAT)

---

## 🎯 Best Practices

### Environment Variables
- ✅ Keep secrets in `.env` (never commit)
- ✅ Provide comprehensive `.env.example`
- ✅ Document what each variable does
- ✅ Use defaults where sensible

### Dependencies
- ✅ Start minimal, add as needed
- ✅ Pin major versions (`>=X.0.0`)
- ✅ Comment out optional dependencies
- ✅ Document why each dependency is needed

### Gitignore
- ✅ Ignore all secrets and credentials
- ✅ Ignore virtual environments
- ✅ Ignore IDE-specific files
- ✅ Don't ignore `.env.example` or templates

### Documentation
- ✅ Keep QUICKSTART focused on setup
- ✅ Include troubleshooting section
- ✅ Show expected outputs
- ✅ Document rate limits and constraints

---

## 🔄 Updating Templates

When you find improvements:
1. Update templates in your project
2. Test thoroughly
3. Submit PR to this repo
4. Help others benefit from your learnings!

---

## 📚 Additional Resources

- [System Instructions](../docs/SYSTEM_INSTRUCTIONS.md) - Complete guide
- [User Prompt Templates](../docs/USER_PROMPT_TEMPLATE.md) - Prompts for building
- [Project Setup Guide](../docs/PROJECT_SETUP.md) - Claude Project configuration
- [Main README](../README.md) - Overview and quick start

---

## 💡 Examples

See the `examples/` directory (when available) for complete working implementations that use these templates.

---

**Questions?** Open an [issue](https://github.com/YOUR_USERNAME/claude-mcp-server-builder/issues) or [discussion](https://github.com/YOUR_USERNAME/claude-mcp-server-builder/discussions)!
