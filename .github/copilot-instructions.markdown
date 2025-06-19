# 🤖 Copilot Global Instructions

These are global workspace instructions that must always be followed by the assistant:

- Always prioritize clarity, performance, and industrial compliance.
- Always save relevant progress, decisions, and insights to the corresponding `gibberlink/*.yaml` files.
- Always consult and update `gibberlink/000_context.yaml` before starting or switching tasks to ensure context consistency.
- ❌ Never suggest MVP hacks or premature optimizations
- ❌ Never skip regulatory or performance checks
- ❌ Never propose solutions that don't scale for 100+ tenants
- ❌ Never remove field-level ACL validation
- ❌ Never ignore GibberLink context loading protocol, especially `000_context.yaml`.
- ❌ Never skip documenting decisions in appropriate YAML files
- ❌ Never proceed without checking current project status.
- ❌ Never proceed without checking current project status in `000_context.yaml`.
- Use YAML structure consistently to log tasks, progress, errors, and insights.
- Never generate throwaway code. All output must match [your_project] architecture and domain model.
- Do not repeat known implementation patterns. Focus on reusable and scalable solutions.

---

# 🔧 GibberLink Protocol - Context Management

## ⚠️ MANDATORY: Load Context First

**BEFORE providing any code suggestions, responses, or solutions, ALWAYS execute:**
1. **Load Active Context**: Read `gibberlink/000_context.yaml` for current task, file, `context_id`, `summary`, `trace_id`, `tags`, and `timestamp`.
2. **Check Index**: Use `gibberlink/009_index.yaml` for quick access to relevant entries.
3. **Update Context**: Append to `gibberlink/000_context.yaml` with:
   - `context_id`: Unique ID (e.g., `CTX20250618_001`).
   - `summary`: Task description (max 50 chars).
   - `current_file`: Active file (e.g., `main.py`).
   - `task`: Task details (max 100 chars).
   - `module`: Module name (e.g., `auth`).
   - `trace_id`: Action link (e.g., `TRC20250618_001`).
   - `timestamp`: ISO 8601 (e.g., `2025-06-18T20:27:00-03:00`).
   - `tags`: Keywords (e.g., `["api", "auth"]`).
   - `priority`: Optional urgency (e.g., `high`, `low`).
   - `related`: Links to entries (e.g., `{ "error": "ERR001" }`).
4. **Read Project State**: Review `gibberlink/002_progress.yaml` for milestones.
5. **Check Recent Context**: Examine `gibberlink/context/[current-month]/` only if referenced in `gibberlink/000_context.yaml`.

### Context Management Guidelines

#### Before Every Response
- **Minimal Context**: Start with `gibberlink/000_context.yaml` and use `gibberlink/009_index.yaml` for targeted lookups.
- **Update Context**: Append task metadata to `gibberlink/000_context.yaml`.
- **Ensure Consistency**: Align suggestions with patterns in `gibberlink/000_context.yaml`.

#### Response Guidelines
- **Context-Aware**: Base responses on `gibberlink/000_context.yaml` and `gibberlink/009_index.yaml`.
- **Reference Work**: Cite related tasks/errors via `trace_id` or `related`.
- **Stay Concise**: Limit context to essentials to save tokens.

#### Progress Tracking
- **Save Decisions**: Log milestones in `gibberlink/002_progress.yaml`, linking to `gibberlink/000_context.yaml`.
- **Document Insights**: Add to `gibberlink/005_lessons_learned.yaml` or `gibberlink/006_insights.yaml`.
- **Track Errors**: Log issues in `gibberlink/003_errors.yaml` with `trace_id`.

#### Code Suggestions
- **Follow Architecture**: Adhere to `gibberlink/001_structure.yaml`.
- **Avoid Anti-Patterns**: Check `gibberlink/004_avoid_list.yaml`.
- **Validate YAML**: Match schemas in `gibberlink/schemas/`.

#### Context Optimization
- **Limit Scope**: Load only files referenced in `gibberlink/000_context.yaml` or `gibberlink/009_index.yaml`.
- **Prioritize Module**: Focus on active module in `gibberlink/000_context.yaml`.
- **Archive Context**: Move entries older than 30 days to `gibberlink/context/[year-month]/`, updating `gibberlink/009_index.yaml`.

---

# 📁 GibberLink File Standards

## ✅ Naming Convention (Mandatory)
- Always update `gibberlink/000_context.yaml` first with task metadata.
- Template for `gibberlink/000_context.yaml`:
  ```yaml
  contexts:
    - context_id: "[Unique ID]"
      summary: "[Task description, max 50 chars]"
      current_file: "[Active file]"
      task: "[Task details, max 100 chars]"
      module: "[Module name]"
      trace_id: "[Unique trace ID]"
      timestamp: "[ISO 8601]"
      tags: ["[keyword1]", "[keyword2]"]
      priority: "[high|medium|low]"
      related: { "[type]": "[ID]" }
  ```
- All files use `.yaml`, not `.yml`.
- Filenames: `NNN_description.yaml`, lowercase, snake_case (e.g., `005_lessons_learned.yaml`).

## 🚫 Prohibited Patterns
- ❌ No `.yml` files to avoid indexing errors.
- ❌ No duplicate prefixes (e.g., `008_summary.yaml` and `008_summary.yml`).
- ❌ No files without numeric prefix.
- ❌ No topic splitting across files.

## 🧠 Context Handling
- Ignore `.yml` files; use only `.yaml`.
- Use `gibberlink/009_index.yaml` for fast lookups, fallback to `gibberlink/000_context.yaml`.
- Track origins with `source_file` and `trace_id` in `gibberlink/000_context.yaml`.

---

# 🔟 GibberLink File Limit (Strict Mode)

## 🎯 Structural Constraint
- Exactly 10 files in `gibberlink/`:
  - `000_context.yaml`: Current task context.
  - `001_structure.yaml`: Project architecture and rules.
  - `002_progress.yaml`: Milestones and task status.
  - `003_errors.yaml`: Known issues.
  - `004_avoid_list.yaml`: Anti-patterns to avoid.
  - `005_lessons_learned.yaml`: Key learnings.
  - `006_insights.yaml`: Technical discoveries.
  - `007_trace.yaml`: Decision traceability.
  - `008_summary.yaml`: Project status summaries.
  - `009_index.yaml`: Index of entries across files.

## 🚫 Do Not Create
- ❌ No prefixes beyond `009_`.
- ❌ No unnumbered or ad hoc files (e.g., `debug.yaml`).
- ❌ No `.yml` variations.
- ❌ No topic splitting.

## 🧠 How to Contribute
- Append to existing files:
  - Context: `gibberlink/000_context.yaml`
  - Insights: `gibberlink/006_insights.yaml`
  - Errors: `gibberlink/003_errors.yaml`
  - Milestones: `gibberlink/002_progress.yaml`
- Update `gibberlink/000_context.yaml` first, then `gibberlink/009_index.yaml`.

## ⚙️ Automation Notes
- Only the 10 files are indexed.
- Non-canonical files are ignored and flagged in `gibberlink/000_context.yaml`.

---

# 🚀 Project Instructions: [YOUR PROJECT]

## 🧭 Overview
[Provide a brief overview of your project, its purpose, and key features.]

---

## 🏗️ Architecture Guidelines
- **Backend**: [Specify backend technologies, e.g., programming language, framework, database].
- **Frontend**: [Specify frontend technologies, e.g., framework, UI libraries].
- **Middleware**: [Specify middleware, e.g., message queues, caching].
- **Deployment**: [Specify deployment strategy, e.g., cloud provider, containerization].
- **Security**: [Specify security measures, e.g., authentication, encryption].
Always follow the architectural principles defined in `gibberlink/001_structure.yaml`.

---

## 🌐 Multi-Tenant Design (Optional)
[If applicable, describe multi-tenancy approach, e.g., data separation, tenant identification.]

---

## 🧠 Team Excellence Standards

### Domain Mastery
- [Understand key domain concepts relevant to the project.]
- [Ensure familiarity with applicable regulations or standards.]
- Never implement logic detached from the project’s business goals.

### Technical Excellence
- Write production-grade code from the first commit.
- [Specify testing strategy, e.g., TDD, unit testing].
- Prioritize performance and scalability.
- Ensure code is modular, reusable, and testable.

---

## 🔩 Role-Specific Instructions
Each role must follow their deliverables and quality benchmarks.

### [Role 1, e.g., Architect]
- [Define responsibilities, e.g., design system architecture].
- [Specify deliverables, e.g., architecture documentation].

### [Role 2, e.g., Developer]
- [Define responsibilities, e.g., implement features].
- [Specify deliverables, e.g., code with tests].

### [Role 3, e.g., QA Engineer]
- [Define responsibilities, e.g., write test cases].
- [Specify deliverables, e.g., test reports].

### [Role 4, e.g., Designer]
- [Define responsibilities, e.g., create UI designs].
- [Specify deliverables, e.g., design prototypes].

---

## 📊 Metrics & Definition of Done

### Technical
- [Metric 1, e.g., API latency: <100ms].
- [Metric 2, e.g., Uptime: 99.9%].

### Business
- [Metric 1, e.g., Feature delivery time reduction: 20%].
- [Metric 2, e.g., User satisfaction: 85%+].

### Team
- [Metric 1, e.g., Zero critical bugs in production].
- [Metric 2, e.g., Code coverage: 90%+].

---

## 🧩 Dev Workflow
- **[Process 1, e.g., Sprint Planning]**: [Describe activity, e.g., review requirements].
- **[Process 2, e.g., Daily Standup]**: [Describe activity, e.g., discuss progress].
- **[Process 3, e.g., Code Reviews]**: [Describe activity, e.g., ensure quality].
- **[Process 4, e.g., Documentation]**: [Describe activity, e.g., include business rationale].

---

## 📁 GibberLink Integration
- Store project-specific rules in `gibberlink/001_structure.yaml`:
  ```yaml
  project:
    name: "[Your Project]"
    description: "[Brief overview]"
    architecture:
      - language: "[e.g., JavaScript]"
      - framework: "[e.g., Node.js]"
    standards:
      - "[e.g., Use camelCase]"
    team:
      roles:
        - role: "[e.g., Developer]"
          responsibilities: ["[e.g., Write code]"]
      metrics:
        - "[e.g., API latency: <100ms]"
  ```
- Always start by loading `gibberlink/000_context.yaml` to ensure context continuity.
- Update `gibberlink/009_index.yaml` to index key project entries.
- Archive old contexts to `gibberlink/context/[year-month]/` for performance.

---

# ✅ Final Mandate
Use the GibberLink protocol to maintain persistent, context-aware development. Every action must build on existing work, ensuring consistency and efficiency. Start by loading `gibberlink/000_context.yaml` to align with the project’s current state.