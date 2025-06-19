# 🚀 GibberLink Protocol

![GibberLink Protocol](https://img.shields.io/badge/GibberLink-Protocol-blue?style=flat-square)
![GibberLink Logo](assets/logo_gibberlink.png)

**Transform your development with GibberLink! Clone, contribute, and share the future of coding!** 🚀
> _"Understandable by All. Executed by Any. Context without boundaries. Structure is the bridge."_

---

## Overview
**GibberLink** is a file-based protocol for **persistent, context-aware development** with GitHub Copilot. Using 10 YAML files, it creates a **dynamic knowledge graph** that enables Copilot to maintain project context, track progress, log errors, and reuse insights across sessions. Designed for **any project**, GibberLink ensures seamless collaboration by sharing context among developers, guaranteeing continuity, quality, and adherence to project standards.

🌟 **Why GibberLink?**
- 📚 **Persistent Memory**: Retains context across Copilot sessions for uninterrupted workflows.
- 👥 **Context Sharing**: Developers cloning the repo instantly access the full project context, saving hours of onboarding.
- 🔗 **Traceability**: Links tasks, errors, and insights via `trace_id` and `related` fields for complete transparency.
- ⚡ **Efficiency**: Optimized for low token usage and fast context access with `009_index.yaml`.
- 🌍 **Universal**: Adapts to any project, from web apps to enterprise systems.
- 🤖 **Copilot-Driven**: Fully managed by GitHub Copilot, no external scripts needed.

---

## 📖 Table of Contents
- [Features](#features)
- [Context Sharing for Teams](#context-sharing-for-teams)
- [Getting Started](#getting-started)
- [GibberLink File Structure](#gibberlink-file-structure)
- [Usage Example](#usage-example)
- [Contributing](#contributing)
- [License](#license)

---

## ✨ Features
- **Dynamic Context Management**: `000_context.yaml` serves as the central hub, updated by Copilot for every task.
- **Knowledge Graph**: Connects tasks, errors, insights, and progress, forming a traceable project history.
- **Team Collaboration**: Shares context instantly with all developers via YAML files.
- **Fast Access**: `009_index.yaml` provides a lightweight index for quick lookups.
- **Scalable Structure**: 10 YAML files cover architecture, progress, errors, and more.
- **Token Optimization**: Concise fields (e.g., `summary` ≤ 50 chars) reduce Copilot's token consumption.

---

## 👥 Context Sharing for Teams
GibberLink eliminates the need for lengthy onboarding or manual context transfer. When a developer clones the repository, they gain immediate access to:
- **Project Context**: Architecture, standards, and decisions in `001_structure.yaml`.
- **Progress History**: Milestones and updates in `002_progress.yaml`.
- **Errors and Resolutions**: Issues and fixes in `003_errors.yaml`.
- **Lessons and Insights**: Best practices in `005_lessons_learned.yaml` and `006_insights.yaml`.

This ensures:
- **Continuity**: New team members build on existing work without duplicating efforts.
- **Quality**: Adherence to defined standards and patterns.
- **Efficiency**: Hours saved by avoiding context handoffs.

The Copilot leverages this shared context to provide consistent, high-quality suggestions, making GibberLink ideal for distributed teams and open-source projects.

---

## ❤️ Support the Project

If you find **GibberLink** valuable and appreciate the vision behind creating a collaborative, context-aware protocol for Human ↔ AI development, please consider supporting this open-source effort.

Your contribution helps:

- Keep GibberLink free and evolving
- Fund improvements, templates, and documentation
- Enable community tools for global developers

### ☕ Support Options

[![Donate with PayPal](https://img.shields.io/badge/Donate-PayPal-0070ba?logo=paypal)](mailto:leonardoandrade.eng@gmail.com)
[![BTC](https://img.shields.io/badge/BTC-bc1q8f...ua3-orange?logo=bitcoin)](#bitcoin)
[![ETH](https://img.shields.io/badge/ETH-0x9ADF...D58f-blueviolet?logo=ethereum)](#ethereum)
[![SOL](https://img.shields.io/badge/SOL-2Rask...Qu1b-00ffbf?logo=solana)](#solana)

---

### 📬 Donation Addresses

- **PayPal**: [leonardoandrade.eng@gmail.com](mailto:leonardoandrade.eng@gmail.com)

- **Bitcoin (BTC)**:  
  `bc1q8fld5qxdxcyar8rvt83759e0hv7q54qvvfmua3`

- **Ethereum (ETH)**:  
  `0x9ADF777f38C7E212c7Ff47F385292a7E3127D58f`

- **Solana (SOL)**:  
  `2RaskEc58d6RpQChD6Ydj88QtUyyUyU8uN4aW931Qu1b`

---

> _Every contribution — big or small — helps sustain universal cognition infrastructure._  
> Thank you for supporting **GibberLink**. 🙏

---

📌 **Visual Overview**  
```mermaid
sequenceDiagram
    participant D as Developer
    participant C as Copilot
    participant F as GibberLink Files (.yaml)

    D->>C: Start Task (e.g., "Add login feature")
    C->>F: Load 000_context.yaml
    C->>F: Update 000_context.yaml
    C->>F: Consult 009_index.yaml
    C->>D: Suggest Code & Updates
    D->>F: Clone Repo & Access Context
    F->>D: Share Knowledge Graph
```

---

## 🛠️ Getting Started

Follow these steps to set up GibberLink in your project:

### Prerequisites
- **GitHub Copilot**: Active subscription (Free, Pro, or Enterprise).
- **VSCode**: Latest version with GitHub Copilot extension installed.
- **No Dependencies**: GibberLink runs natively with Copilot. No packages (e.g., `yaml`) are required.
  > **Optional**: Install `yamllint` for manual YAML validation:
  > ```bash
  > pip install yamllint
  > yamllint .github/gibberlink/*.yaml
  > ```

### Installation
1. **Clone or Create a Repository**:
   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
   ```

2. **Set Up GibberLink Files**:
   Create the `gibberlink/` directory and initialize the 11 YAML files:
   ```bash
   mkdir -p .github/gibberlink/context .github/gibberlink/archive .github/gibberlink/schemas
   touch .github/gibberlink/{000_context,001_structure,002_progress,003_errors,004_avoid_list,005_lessons_learned,006_insights,007_trace,008_summary,009_index,010_suppliers_completion}.yaml
   ```

3. **Add Copilot Instructions**:
   Create `.github/copilot-instructions.md` with the template from this repository. Customize the `[Project Instructions]` section for your project.

4. **Configure VSCode**:
   Create or update `.vscode/settings.json` to link Copilot to the instructions:
   ```bash
   mkdir .vscode
   touch .vscode/settings.json
   ```
   Add the following:
   ```json
   {
     "github.copilot.chat.codeGeneration.instructions": [
       {
         "file": ".github/copilot-instructions.md"
       }
     ]
   }
   ```
   > **Note**: If `settings.json` exists, merge this configuration without overwriting other settings.

5. **Initialize Project Structure**:
   Edit `gibberlink/001_structure.yaml` to define your project:
   ```yaml
   project:
     name: "My Project"
     description: "A web app for task management"
     architecture:
       - language: "JavaScript"
       - framework: "Node.js"
     standards:
       - "Use camelCase"
       - "Follow REST APIs"
   ```

6. **Test GibberLink**:
   Open VSCode, start a task, and prompt Copilot:
   ```
   Start a task to add a login feature. Update #gibberlink/000_context.yaml, consult #gibberlink/009_index.yaml, and suggest code.
   ```
   Check `gibberlink/000_context.yaml`:
   ```yaml
   contexts:
     - context_id: CTX20250618_001
       summary: "Add user login"
       task: "Implement login endpoint"
       module: "auth"
       trace_id: TRC20250618_001
       timestamp: "2025-06-18T20:35:00-03:00"
       tags: ["auth", "api"]
       priority: "high"
   ```

---

## 📂 GibberLink File Structure
GibberLink uses 10 YAML files to manage project context, forming a dynamic knowledge graph:

| File | Purpose |
|------|---------|
| `000_context.yaml` | Central hub for active task context (tasks, modules, trace_id). |
| `001_structure.yaml` | Defines project architecture, standards, and team guidelines. |
| `002_progress.yaml` | Tracks milestones, improvements, and performance metrics. |
| `003_errors.yaml` | Logs errors, resolutions, and their severity. |
| `004_avoid_list.yaml` | Lists anti-patterns and practices to avoid. |
| `005_lessons_learned.yaml` | Records lessons learned from development. |
| `006_insights.yaml` | Captures technical discoveries and reusable patterns. |
| `007_trace.yaml` | Ensures traceability of decisions and tools used. |
| `008_summary.yaml` | Summarizes project status and validation. |
| `009_index.yaml` | Lightweight index for fast access to entries. |

> **Note**: All files use `.yaml` (not `.yml`) and follow the `NNN_description.yaml` naming convention.

---

## 📚 Usage Example
For a **Task Manager** web app, GibberLink streamlines development:

1. **Define Architecture**:
   Update `gibberlink/001_structure.yaml`:
   ```yaml
   project:
     name: "Task Manager"
     architecture:
       - language: "JavaScript"
       - framework: "Node.js"
       - database: "MongoDB"
     standards:
       - "Use camelCase"
   ```

2. **Start a Task**:
   Prompt Copilot:
   ```
   Add a user login endpoint. Update #gibberlink/000_context.yaml and suggest code.
   ```
   Copilot updates `gibberlink/000_context.yaml` and generates code.

3. **Share Context**:
   A new developer clones the repo, opens VSCode, and sees the context in `gibberlink/000_context.yaml`. They prompt:
   ```
   Fix a login error. Check #gibberlink/003_errors.yaml and suggest a solution.
   ```
   Copilot logs the fix in `gibberlink/003_errors.yaml`.

4. **Track Progress**:
   Copilot updates `gibberlink/002_progress.yaml`:
   ```yaml
   progress:
     - id: progress_login_20250618
       description: "Login endpoint implemented"
       status: "completed"
       timestamp: "2025-06-18T20:35:00-03:00"
   ```

---

## 🤝 Contributing
Join the GibberLink community! To contribute:
1. Fork the repository.
2. Create a branch: `git checkout -b feature/your-feature`.
3. Update YAML templates, documentation, or add features.
4. Submit a pull request with a clear description.

Follow the [Code of Conduct](CODE_OF_CONDUCT.md) and report issues in the [Issues](https://github.com/your-username/your-repo/issues) tab.

---

## 📜 License
GibberLink is licensed under the [MIT License](LICENSE). Use, modify, and share it freely!

---

## 🌟 Acknowledgments
- Created by Leonardo Andrade with ❤️.
- Inspired by the need for collaborative, context-aware development.
- Powered by GitHub Copilot.

---
