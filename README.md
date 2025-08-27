# Claude Code Custom Configuration Repository

A comprehensive Claude Code configuration repository featuring specialized agents and custom commands for enhanced development workflow.

## 🚀 Overview

This repository contains:
- **120+ Specialized Agents** - Expert AI agents for every development domain
- **20+ Custom Commands** - Streamlined workflows for common tasks
- **Multi-Agent Orchestration** - Coordinate multiple agents for complex projects

## 📦 Installation

### Install Claude Code

First, install Claude Code CLI:

```bash
# Install via npm
npm install -g @anthropic/claude-code

# Or install via pip
pip install claude-code

# Or download binary from GitHub releases
# https://github.com/anthropics/claude-code/releases
```

### Setup This Configuration

1. **Clone this repository to your Claude configuration directory:**
```bash
# Clone to default Claude config location
git clone https://github.com/your-username/claude-config ~/.claude

# Or clone to custom location and set environment variable
git clone https://github.com/your-username/claude-config /path/to/config
export CLAUDE_CONFIG_PATH=/path/to/config
```

2. **Initialize Claude Code:**
```bash
claude-code init
```

3. **Verify installation:**
```bash
claude-code --version
claude-code list-agents
claude-code list-commands
```

## 🤖 Specialized Agents

### Core Development Agents (120+ Available)

#### **Backend & API Development**
- `backend-developer` - Server-side APIs and microservices
- `api-designer` - REST and GraphQL API architecture
- `microservices-architect` - Distributed systems design
- `database-administrator` - Database optimization and management

#### **Frontend & Mobile**
- `frontend-developer` - React, Vue, Angular development
- `mobile-developer` - iOS, Android, React Native, Flutter
- `electron-pro` - Cross-platform desktop applications
- `nextjs-developer` - Next.js full-stack development

#### **DevOps & Infrastructure**
- `devops-engineer` - CI/CD, containerization, automation
- `cloud-architect` - AWS, Azure, GCP architecture
- `kubernetes-specialist` - Container orchestration
- `terraform-engineer` - Infrastructure as Code

#### **Security & Quality**
- `security-engineer` - Security implementation and auditing
- `penetration-tester` - Ethical hacking and vulnerability assessment
- `code-reviewer` - Code quality and best practices
- `testing-specialist` - Test automation and QA

#### **AI/ML & Data**
- `ai-engineer` - AI system design and implementation
- `ml-engineer` - Machine learning model deployment
- `data-scientist` - Data analysis and insights
- `data-engineer` - Data pipelines and architecture

### Quick Agent Selection Guide

| Need | Agent |
|------|--------|
| Build REST API | `backend-developer` |
| Create React UI | `frontend-developer` |
| Deploy to cloud | `devops-engineer` |
| Security review | `security-engineer` |
| Database optimization | `database-administrator` |
| Mobile app | `mobile-developer` |
| AI/ML implementation | `ai-engineer` |

### Using Agents

```bash
# Launch a specialized agent
claude-code agent backend-developer "Build a REST API for user management"

# Use multiple agents for complex tasks  
claude-code agent frontend-developer "Create React dashboard UI"
claude-code agent backend-developer "Build supporting API endpoints"
```

## ⚡ Custom Commands

### Project Management Commands

#### `/create <project-idea>`
Creates new project with multi-agent orchestration:
- Generates project structure and specifications
- Analyzes complexity and selects appropriate agents
- Creates phase-based task distribution
- Sets up project registry and tracking

```bash
claude-code /create "E-commerce platform with React frontend and Node.js backend"
```

#### `/task <feature-description>`  
Adds features to active project:
- Integrates with existing architecture
- Updates task specifications
- Coordinates agent implementation

```bash
claude-code /task "Add payment gateway integration"
```

#### `/deploy [environment]`
Deploys project to specified environment:
- Analyzes deployment requirements
- Generates Docker/container configurations
- Sets up CI/CD pipelines
- Supports AWS, GCP, Azure, Vercel, etc.

```bash
claude-code /deploy production
```

### Development Commands

#### `/generate-agent <specialization>`
Creates custom agent for specific needs:
- Generates agent definition file
- Sets up appropriate tools and permissions
- Updates agent registry

```bash
claude-code /generate-agent "blockchain-smart-contracts"
```

#### `/security-review [project]`
Comprehensive security audit:
- Code vulnerability scanning
- Dependency security audit
- Git history security check
- Generates security compliance report

```bash
claude-code /security-review my-project
```

#### `/docs`
Generates project documentation:
- API documentation
- Architecture diagrams
- Setup instructions
- Deployment guides

### Utility Commands

- `/clone-website` - Clone and analyze website structure
- `/configure-routing` - Setup application routing
- `/monitor` - Setup monitoring and logging
- `/rollback` - Rollback failed deployments
- `/upload` - Upload and deploy files


## 🛠️ Advanced Usage

### Multi-Agent Orchestration

Coordinate multiple agents for complex projects:

```bash
# Create project with automatic agent selection
claude-code /create "Full-stack e-commerce with React, Node.js, and PostgreSQL"

# This automatically assigns:
# - frontend-developer for React UI
# - backend-developer for Node.js API  
# - database-specialist for PostgreSQL
# - devops-engineer for deployment
```

### Project Registry Management

Track multiple projects:

```bash
# View active projects
claude-code projects

# Switch active project  
claude-code projects switch my-project

# View project status
claude-code projects status
```

### Custom Agent Development

Create specialized agents for your domain:

```bash
# Generate new agent
claude-code /generate-agent "shopify-theme-developer"

# Edit agent configuration
vim ~/.claude/agents/shopify-theme-developer.md

# Use new agent
claude-code agent shopify-theme-developer "Create responsive product page"
```

## 🔧 Configuration

### Environment Variables

```bash
# Custom config path
export CLAUDE_CONFIG_PATH=/path/to/config

# Agent timeout settings
export CLAUDE_AGENT_TIMEOUT=300

# Logging level
export CLAUDE_LOG_LEVEL=info
```

### Agent Configuration

Each agent can be configured in `agents/[agent-name].md`:

```markdown
---
name: agent-name
description: Agent description
tools: [Read, Write, Edit, Bash]
timeout: 300
---

Agent instructions and guidelines...
```

### Command Configuration

Custom commands in `commands/[command-name].md`:

```markdown
---
description: Command description
argument-hint: <arguments>
allowed-tools: [Bash, Read, Write]
---

Command implementation steps...
```

## 📚 Examples

### Example 1: Full-Stack Web Application

```bash
# Create project
claude-code /create "Task management app with React frontend and Express backend"

# Add authentication
claude-code /task "Implement JWT authentication"

# Add real-time features  
claude-code /task "Add real-time notifications with WebSocket"

# Deploy
claude-code /deploy staging
```

### Example 2: Mobile App Development

```bash
# Create mobile project
claude-code /create "React Native food delivery app"

# Add maps integration
claude-code /task "Integrate Google Maps for delivery tracking"

# Add payment processing
claude-code /task "Implement Stripe payment integration"
```

### Example 3: Microservices Architecture

```bash
# Create microservices project
claude-code /create "E-commerce microservices with Docker and Kubernetes"

# Add service
claude-code /task "Add inventory management service"

# Setup monitoring
claude-code /monitor
```

## 🔒 Security

### Security Features

- **Code Vulnerability Scanning** - Automated security review
- **Dependency Auditing** - Check for known vulnerabilities
- **Secret Detection** - Prevent credential leaks
- **Access Control** - Agent permission management

### Security Commands

```bash
# Full security review
claude-code /security-review

# Check dependencies  
claude-code /security-review --deps-only

# Scan for secrets
claude-code /security-review --secrets
```

## 🤝 Contributing

1. **Fork this repository**
2. **Add your custom agents or commands**
3. **Test your contributions thoroughly**
4. **Submit pull request with description**

### Agent Contributions

When contributing agents:
- Include comprehensive documentation
- Add usage examples
- Follow naming conventions
- Test thoroughly

### Command Contributions

When contributing commands:
- Include help documentation
- Add error handling
- Follow security best practices
- Include examples

## 📄 License

This configuration repository is licensed under MIT License. See LICENSE file for details.

## 🆘 Support

- **Documentation:** [Claude Code Docs](https://docs.anthropic.com/claude-code)
- **Issues:** [GitHub Issues](https://github.com/anthropics/claude-code/issues)
- **Community:** [Discord](https://discord.gg/anthropic)

---

**Ready to supercharge your development workflow with Claude Code?** 🚀

Start with `claude-code /create "your project idea"` and let our specialized agents handle the complexity while you focus on innovation.