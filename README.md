# SAFe Agent

A SAFe (Scaled Agile Framework) project management system featuring specialized AI agent personas for an agile team.

## Purpose

This project provides a collection of role-based AI agents designed to support different aspects of software development within a SAFe framework. Each agent embodies a specific persona with tailored expertise, communication style, and responsibilities.

## Available Personas

- **Software Architect** - System design and architecture decisions
- **Backend Developer** - API design, business logic, and data modeling
- **Frontend Developer** - UI/UX and client-side development
- **Code Reviewer** - Code quality, security, and best practices
- **Software Tester** - QA, testing strategies, and automation
- **Technical Writer** - Documentation and user guides
- **Security Master** - Application security and threat modeling
- **DevOps Engineer** - CI/CD pipelines, infrastructure automation, and deployment
- **Release Train Engineer (RTE)** - SAFe alignment and flow facilitation
- **Product Owner** - Backlog management and prioritization
- **Team Coach** - Agile coaching and process improvement

Each persona references shared project context including Product Blueprint, Architecture Document, Team Backlog, Development Log, and User Guide to maintain alignment with the a team's objectives.

## Configuration

### Project-Level Configuration (.amazonq)

The `.amazonq/` directory contains project-specific configurations that apply to all team members working on this project:

- `.amazonq/rules/` - Contains project-level rules and context that are automatically included in every chat and inline chat request
- `.amazonq/rules/persona.md` - Defines the available AI personas and their behaviors
- `.amazonq/rules/project-context.md` - Shared project context referenced by all personas

To use the configuration, copy the `.amazonq` folder to the root of your project.

### Global Configuration (~/.aws/amazonq)

The `~/.aws/amazonq/` directory contains user-specific global configurations:

- `~/.aws/amazonq/prompts/` - Personal saved prompts that can be referenced with `@prompt` in chat messages
- `~/.aws/amazonq/agents/` - Agent configurations for IDE usage
- `~/.aws/amazonq/cli-agents/` - Agent configurations for CLI usage
- `~/.aws/amazonq/default.json` - Legacy MCP config files

Global settings that apply across all projects for the individual user

To use the global configuration, copy the `.aws` folder to your `$HOME` directory.

#### 🔍 How Agent Config References Global MCP (`~/.aws/amazonq/default.json`)

- **useLegacyMcpJson** Field

In your agent’s JSON config, there’s a boolean field `useLegacyMcpJson`.
If you set `useLegacyMcpJson: true`, the agent will automatically include MCP servers from the legacy MCP config files, including:

- `~/.aws/amazonq/mcp.json` (global)
- `~/.aws/amazonq/default.json` (global)
Since the IDE now stores MCP config in ~/.aws/amazonq/default.json (which replaced mcp.json), that will be picked up too.

**No Need to Replicate the Server in mcpServers**

Because of `useLegacyMcpJson`, you don’t need to re-declare the same MCP servers in the agent’s mcpServers if they’re already defined in your global MCP config (~/.aws/amazonq/default.json).

If you do declare servers in mcpServers, those are added on top of what’s inherited (unless names conflict).

When to Use mcpServers in Agent Config

Use it when:

- You want agent-specific MCP servers (i.e., only that agent should talk to a particular MCP)

- You need a different configuration (command, URL, args) than what’s in the global default.json

- You want to override or supplement global servers
