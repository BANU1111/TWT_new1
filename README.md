# Document Quality Checker

## Problem Statement

Technical documentation teams often spend significant time manually reviewing Microsoft Word documents for formatting and structural issues before publication. Common issues include:

- Missing Heading 1
- Incorrect heading hierarchy
- Skipped heading levels
- Inconsistent document structure

Manual reviews are repetitive, time-consuming, and prone to human error, especially when handling a large number of documents.

---

# Project Scope

The Document Quality Checker automates the review of Word (.docx) documents by analyzing their heading structure and generating a quality report.

Current capabilities include:

- Reading Microsoft Word (.docx) documents
- Validating heading hierarchy
- Detecting structural inconsistencies
- Generating an HTML quality report
- Returning a JSON summary through an MCP tool

This proof-of-concept focuses only on document structure and heading validation.

---

# Project Structure

```
document-quality-checker/
│
├── server/
│   └── index.py
│
├── src/
│   ├── docx_reader.py
│   ├── heading_checker.py
│   └── report_generator.py
│
├── output/
│
├── .claude/
│
└── README.md
```

---

# Prerequisites

- Python 3.11 or later
- Microsoft Word (.docx) document
- MCP 2.0.0
- Claude Code (for MCP integration)

Install dependencies

```bash
pip install -r requirements.txt
```

---

# Setup

Clone the repository

```bash
git clone <repository-url>
cd document-quality-checker
```

Install dependencies

```bash
pip install -r requirements.txt
```

Configure the MCP server

```json
{
  "mcpServers": {
    "document-quality-checker": {
      "command": "py",
      "args": [
        "-3",
        "server/index.py"
      ]
    }
  }
}
```

---

# Running the Proof of Concept

Start Claude Code.

Invoke the MCP tool:

```
check_document_quality
```

Input

```
document_path
```

Example

```
D:\Documents\Healthy_Lifestyle_Unformatted.docx
```

The tool generates:

- HTML quality report
- JSON summary

---

# Output

Example JSON

```json
{
  "status": "success",
  "report_path": "...",
  "total_findings": 7,
  "error_count": 0,
  "warning_count": 1,
  "info_count": 6
}
```

---

# What is Automated

The proof-of-concept automatically performs the following tasks:

- Reads Word documents
- Detects heading hierarchy issues
- Detects missing Heading 1
- Detects multiple Heading 1 sections
- Generates an HTML report
- Returns a structured JSON summary through the MCP interface

---

# What Still Requires Human Review

The current implementation does not evaluate document quality beyond structure.

A technical writer should still review:

- Grammar
- Spelling
- Technical accuracy
- Completeness
- Images
- Tables
- Captions
- Writing style
- Consistency of terminology
- Compliance with company documentation standards

---

# Known Limitations

Current limitations include:

- Supports only Microsoft Word (.docx) files.
- Does not check fonts or formatting consistency.
- Does not validate tables or images.
- Does not verify caption styles.
- Does not detect broken references or hyperlinks.
- Does not review document content or technical correctness.
- Relies on correctly applied Microsoft Word heading styles.

If headings are manually formatted instead of using Word Heading styles, they may not be detected correctly.

---

# Workshop Learnings Applied

This project applies several concepts learned during the workshop:

- MCP (Model Context Protocol) server development
- Claude Code integration
- Tool registration
- Prompt-driven workflows
- Modular software design
- JSON-based communication
- Proof-of-concept development
- AI-assisted automation for documentation workflows

---

# Future Enhancements

Planned improvements include:

- Font consistency checking
- Paragraph spacing validation
- Caption style validation
- Table style validation
- Image validation
- Broken link detection
- Grammar checking
- Automatic document correction
- PDF support
- Batch document processing

---

