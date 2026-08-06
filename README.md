# Claude Marketplace

A collection of Claude plugins, MCP tools, skills, prompts, and agents for technical writing and documentation.

## About

This repository serves as a marketplace for reusable Claude resources.

The goal is to simplify technical documentation workflows by providing ready-to-use AI-powered tools.

## Available Plugins

### 📄 Document Quality Checker

An MCP-powered plugin for reviewing Microsoft Word (.docx) documents.

Features:
- Heading hierarchy validation
- Document structure analysis
- HTML report generation
- JSON summary
- Claude Skill integration

## Repository Structure

.claude-plugin
├── marketplace.json
├── plugins
│   └── document-quality-checker
│       ├── plugin.json
│       ├── commands
│       │   ├── check-document.md
│       │   └── generate-report.md
│       ├── skills
│       ├── prompts
│       ├── agents
└── README.md

Each plugin contains:

- plugin.json
- README.md
- commands
- skills
- prompts
- agents
- mcp

## Upcoming Plugins
- Grammar Review Assistant
- Technical Writing Assistant
