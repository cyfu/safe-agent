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
- Global settings that apply across all projects for the individual user

To use the global configuration, copy the `.aws` folder to your `$HOME` directory.