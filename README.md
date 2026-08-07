# DocAssist AI – Intelligent Technical Documentation Quality Checker

## Overview

DocAssist AI is an AI-powered document quality checker that automates the pre-review process for Microsoft Word technical documents. It analyzes document structure, validates documentation standards, and generates a detailed HTML quality report to help technical writers identify issues before manual review.

The solution is implemented as a Python-based MCP (Model Context Protocol) server that exposes a `check_document_quality` tool, enabling Claude Code to invoke the document analysis workflow directly.

---

# Problem Statement

Technical documentation often requires multiple review cycles to identify formatting and structural issues before publication. Manual reviews are repetitive, time-consuming, and susceptible to human error.

Common issues include:

- Incorrect heading hierarchy
- Missing or inconsistent formatting
- Empty headings
- Improper document structure
- Style inconsistencies
- Documentation standard violations

This project automates the document pre-review process by performing quality checks and generating a structured report with actionable findings.

---

# Target Users

- Technical Writers
- Documentation Engineers
- Technical Publications Teams
- Documentation Reviewers
- Product Documentation Managers

---

# Features

- Microsoft Word (.docx) document analysis
- Heading hierarchy validation
- Empty heading detection
- Document structure validation
- HTML quality report generation
- JSON summary output
- MCP Server integration
- Claude Skill integration

---

# Project Workflow

```text
Word Document (.docx)
        │
        ▼
Document Reader
        │
        ▼
Heading Validation
        │
        ▼
Quality Analysis
        │
        ▼
HTML Report Generation
        │
        ▼
JSON Summary
```

---

# Project Structure

```text
document-quality-checker/
│
├── .claude/
│   ├── mcp.json
│   └── skills/
│       └── document-quality-checker.md
│
├── input/
│   └── formatted.docx
│
├── output/
│   └── formatted_quality_report.html
│
├── server/
│   └── index.py
│
├── src/
│   ├── docx_reader.py
│   ├── heading_checker.py
│   └── report_generator.py
│
├── tests/
│
└── README.md
```

---

# Technology Stack

| Component | Technology |
|------------|------------|
| Language | Python 3.14 |
| MCP SDK | mcp 2.0.0 |
| Document Processing | python-docx |
| Report Generation | HTML |
| AI Integration | Claude Skills |
| MCP Server | Official MCP SDK |
| Version Control | GitHub |

---

# Installation

Clone the repository.

```bash
git clone https://github.com/<your-username>/document-quality-checker.git

cd document-quality-checker
```

Install dependencies.

```bash
pip install -r requirements.txt
```

---

# MCP Server Configuration

Register the MCP server with Claude Code.

```bash
claude mcp add --scope project document-quality-checker -- C:\Windows\py.exe -3 D:\document-quality-checker\server\index.py
```

Approve the server when prompted.

Verify the registration.

```bash
claude mcp list
```

Expected output:

```text
document-quality-checker
✔ Connected
```

---

# Running the MCP Server

The server is automatically started by Claude Code.

To test manually:

```bash
py -3 server/index.py
```

---

# Available MCP Tool

## check_document_quality

Analyzes a Microsoft Word document and generates a quality report.

### Input

```json
{
  "document_path": "input/formatted.docx"
}
```

### Output

```json
{
  "status": "success",
  "report_path": "output/formatted_quality_report.html",
  "total_findings": 0,
  "error_count": 0,
  "warning_count": 0,
  "info_count": 0
}
```

---

# Example Usage

Ask Claude Code:

```text
Use the check_document_quality tool to analyze input/formatted.docx.
```

Example response:

```json
{
  "status": "success",
  "report_path": "D:\\document-quality-checker\\output\\formatted_quality_report.html",
  "total_findings": 0,
  "error_count": 0,
  "warning_count": 0,
  "info_count": 0
}
```

---

# Components

## DocxReader

Reads Microsoft Word documents and extracts document content.

### Responsibilities

- Read .docx files
- Extract paragraphs
- Preserve document structure

---

## HeadingChecker

Validates heading hierarchy and document organization.

Checks include:

- Empty headings
- Heading hierarchy
- Missing Heading 1
- Skipped heading levels
- Multiple top-level headings
- Document structure validation

---

## HTMLReportGenerator

Generates an HTML report containing:

- Summary statistics
- Error count
- Warning count
- Information count
- Detailed findings

---

# Workshop Learnings Applied

This project applies several concepts covered during the AI workshop.

## Prompt Engineering

Designed structured prompts to perform document quality validation and generate consistent outputs.

## Claude Skills

Created a reusable Document Quality Checker Skill that guides Claude through the review workflow.

## MCP Server

Implemented a Python-based MCP server using the official MCP SDK to expose document quality analysis as a reusable tool.

## AI Workflow

Automated the complete workflow:

```text
Word Document
      │
      ▼
Quality Analysis
      │
      ▼
HTML Report
      │
      ▼
JSON Summary
```

## GitHub

Maintained the complete source code, documentation, and proof-of-concept in a public repository.

---

# What is Automated

The system automatically:

- Reads Microsoft Word documents
- Validates heading hierarchy
- Detects structural issues
- Generates HTML reports
- Returns JSON summaries
- Integrates with Claude through MCP

---

# What Requires Human Review

The proof-of-concept does **not** automatically correct documents.

Human reviewers are responsible for:

- Accepting or rejecting recommendations
- Editing document content
- Technical accuracy review
- Language improvements
- Compliance validation

---

# Known Limitations

Current limitations include:

- Supports only Microsoft Word (.docx) documents
- Focuses primarily on document structure
- Does not automatically correct issues
- Does not validate technical correctness
- Does not perform grammar or spelling checks
- No Microsoft Word add-in
- No cloud deployment

---

# Future Enhancements

- Automatic issue correction
- Grammar and readability analysis
- DITA XML support
- PDF support
- Confluence integration
- Microsoft Word Add-in
- Company terminology validation
- AI-powered document rewriting

---

# Success Criteria

The project is considered successful if it:

- Successfully processes Microsoft Word documents
- Detects documentation quality issues
- Generates HTML reports
- Returns structured JSON summaries
- Exposes functionality through an MCP server
- Integrates successfully with Claude Code

---

