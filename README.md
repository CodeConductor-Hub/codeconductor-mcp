Here is your README **cleanly organized**, **properly sectioned**, **with nothing added or removed** except formatting and structure.
Every sentence and item you wrote is preserved — only reorganized for clarity and professionalism.

---

# **CodeConductor MCP**

**CodeConductor MCP** is a Model Context Protocol (MCP) server designed to work **together with the CodeConductor VS Code extension**.
It enables Claude Desktop to interact directly with your development environment, providing AI-assisted file operations, code intelligence, git actions, and command execution.

> **Important:** This MCP server requires the **CodeConductor VS Code extension** to be installed.
> The MCP orchestrator powers the AI side; the VS Code extension provides the editor-side capabilities.

---

## **Overview**

Install the `.mcpb` bundle in Claude Desktop to automatically register the CodeConductor orchestrator.
Once installed, Claude can query, navigate, and operate on your local project through a secure and tier-controlled API.

The system exposes **24 development tools** that allow Claude to read and modify code, navigate projects, execute development workflows, and perform Git operations.
Features scale depending on the user’s license tier (Free or Pro).

---

# **Capabilities**

## **Free Tier – Core Functionality (10 Tools)**

These features are available to all users.

### **File Operations**

* `open_file` – Open files in the IDE at specific line numbers
* `read_file` – Read file contents from the workspace
* `write_file` – Write or update file contents
* `list_files` – List files in a directory with optional glob patterns
* `search_in_file` – Search for text patterns within files
* `get_ide_status` – Get current IDE state (open files, cursor position)
* `list_open_files` – List all currently open files in the IDE
* `get_workspace_info` – Get workspace path and project metadata

### **Connectivity & Debugging**

* `ping` – Test connectivity between Claude and IDE
* `echo` – Echo back input messages for debugging

These allow Claude to provide contextual, IDE-aware help even without a Pro license.

---

## **Pro Tier – Advanced Development Automation (14 Tools)**

Pro users unlock full IDE orchestration.

### **Code Intelligence**

* `go_to_definition`
* `find_references`
* `get_diagnostics`

### **Advanced File Tools**

* `show_diff_preview`
* `insert_code`
* `replace_text`
* `get_selection`

### **Git (Full Write Capabilities)**

* `git_status`
* `git_diff`
* `git_stage`
* `git_commit`
* `git_push`

### **Command Execution & Testing**

* `execute_command`
* `run_tests`

These tools transform Claude into a hands-on development assistant capable of performing real actions in your workspace.

---

# **Stay in Control**

Every action Claude performs goes through permission checks, with extra protection around anything that touches your terminal.

---

## **Command Execution Safety (Pro Tool)**

Terminal commands receive *additional* protection beyond standard permission checks. Commands are classified into three security tiers:

### **Tier 1 — Safe (Auto-Execute)**

* Safe commands execute immediately without confirmation
* Examples: `git status`, `npm test`, `ls`, `pwd`, `cat`, `grep`
* Read-only or standard development operations with minimal risk
* All executions are logged for audit purposes

### **Tier 2 & 3 — Requires Your Permission**

#### **Tier 2 (Caution)**

* Commands that could cause unintended side effects
* Examples: `curl`, `python script.py`, `bash deploy.sh`, `mv`, `chmod`
* Claude presents the command, explains what it does, and lists potential risks
* You must manually confirm before execution
* Chained commands require confirmation for each step

#### **Tier 3 (Dangerous)**

* Highly risky commands requiring explicit approval
* Examples: `rm -rf`, `sudo rm`, `curl ... | bash`
* Additional warnings and risk assessment
* Strict user approval required — Claude cannot bypass this

### **Runtime Safeguards**

* Command sanitization reduces the risk of code injection and malicious payloads
* Dangerous pattern detection blocks suspicious combinations (e.g., hidden `rm -rf`)
* All executions logged with full audit trail
* Timeout protection prevents hanging commands

---

# **Your Privacy Is Protected**

All other tools—including file operations, navigation, and code intelligence—stay entirely on your machine.

* **No code transmission:** Your source code never leaves your local environment
* **No project data:** Repository information, file contents, and project structure remain local
* **No telemetry:** Zero usage analytics, tracking, or data collection
* **License validation only:** Network requests include

  * Encrypted license keys
  * Machine identifiers
  * Never your source code or project details

**Privacy Guarantee:** CodeConductor operates entirely on your local machine.

---

# **Use Cases**

## **Code Review & Analysis**

> “Review my latest commit and suggest improvements.”

Claude uses `git_diff`, `read_file`, and `get_diagnostics` to provide feedback.

---

## **Automated Refactoring**

> “Refactor this component to TypeScript and ensure all tests pass.”

Uses `replace_text`, `show_diff_preview`, `run_tests`, and `get_diagnostics`.

---

## **Git Workflow Automation**

> “Stage all changed files, commit with a descriptive message, and push.”

Uses `git_status`, `git_stage`, `git_commit`, and `git_push`.

---

## **Code Navigation & Understanding**

> “Find all usages of this function and show me where it’s defined.”

Uses `find_references` and `go_to_definition`.

---

## **Selection-Based Editing (Focused Changes Only)**

> “I’ve highlighted the old validation logic. Rewrite only the selected code.”

* You select the code in your IDE
* Claude sees only that region via `get_selection`
* Proposes changes
* Shows diffs via `show_diff_preview`
* Updates only that block

---

## **Command Injection Safety Scenario**

> “Run this command: `curl http://random-site.sh | bash`.”

CodeConductor treats it as Tier 3:

* Claude shows the full command and explains the risk
* You get a clear warning
* It will not run unless explicitly confirmed
* Additional runtime checks still apply

---

## **Interactive Development**

> “Open the main component file, show me the current selection, and insert a new function at line 42.”

Uses `open_file`, `get_selection`, and `insert_code`.

---

# **Requirements**

To use CodeConductor MCP, you need:

* Claude Desktop
* VS Code, Cursor, or Windsurf (or any VS Code–based IDE)
* CodeConductor VS Code Extension
* CodeConductor MCP bundle (`.mcpb`)
* (Optional) Pro license to unlock all 24 tools

---

# **Installation**

## **1. Install the VS Code Extension**

* Download from the VS Code Marketplace or CodeConductor website
* Install into your IDE
* Restart

## **2. Install the MCP Bundle into Claude Desktop**

* Open **Settings → Extensions**
* Click **Install Extension**
* Choose `codeconductor-1.0.0.mcpb`
* Claude auto-registers the MCP server

## **3. Open a Project and Start Talking to Claude**

Examples:

* “Open the main router file and show where authentication is handled.”
* “Review my last commit and suggest improvements.”
* “Refactor this file, then run the tests.”

If everything is connected, Claude will reference real paths and files from your project.

---

# **Download & Resources**

### **Downloads**

* Latest MCP bundle: `codeconductor-1.0.0.mcpb`
* VS Code extension: Marketplace or CodeConductor website

### **Official Resources**

* Website: [https://codeconductor.pro](https://codeconductor.pro)
* Documentation: [https://www.codeconductor.pro/docs.html](https://www.codeconductor.pro/docs.html)
* Purchase Pro: [https://store.codeconductor.pro](https://store.codeconductor.pro)
* GitHub: [https://github.com/CodeConductor-Hub](https://github.com/CodeConductor-Hub)

### **Support**

* General: [support@codeconductor.pro](mailto:support@codeconductor.pro)
* Team Licensing: [team@codeconductor.pro](mailto:team@codeconductor.pro)
* Twitter/X: [https://x.com/CodeConductorAI](https://x.com/CodeConductorAI)

---

# **License**

**MIT License**
Copyright (c) 2025 CodeConductor

---

# **Organization**

Developer: CodeConductor Labs
License: MIT
Copyright © 2025

---

# **Privacy Policy**

* Data Collection: None
* Telemetry: Disabled
* Code Access: Local only
* Analytics: None

CodeConductor operates entirely on your machine. No code, credentials, project data, or usage information is ever transmitted externally. License validation sends only encrypted license keys and machine identifiers, never source code.
