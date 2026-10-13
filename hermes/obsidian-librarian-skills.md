# Obsidian Vault Librarian Skills & Tools — Ranked Findings

Compiled for Moto Gringo Productions / personal vault style. Focus: agentic librarian / vault management, local-first, skills-based, and automation-friendly.

## Ranking Criteria
1. **Local-first / self-hosted fit** — works with Netbird-only, no cloud lock-in
2. **Agent/Skills model** — uses `.agents/skills/<name>/SKILL.md` or equivalent
3. **Vault operations** — read/search/write with approval, link hygiene, MOC building
4. **Mobile parity** — works on phone too
5. **Integration** — MCP, OpenAI-compatible API, Ollama/LM Studio support

---

### 1. Vault Librarian — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vault-librarian
**Why it fits:** Built-in agent living in Obsidian. Plain-language search with `find`/`grep`/`read` tools, answers with source lines, changes only after approval. Skills system via `.agents/skills/<name>/SKILL.md`. Works on desktop + mobile, any OpenAI-compatible endpoint. OpenAI-compatible provider config, per-tool permissions.

**Strengths:** Local-first, no index build, rewind conversations, MCP server support, WebDAV storage.
**Trade-offs:** Needs a model provider; you supply API.

---

### 2. Vault Operator — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vault-operator
**Why it fits:** Agentic AI operating layer for vault. Plans, searches, reads, writes, reports back. Every action visible, writes need approval, one-click undo. BYOK + MCP. Works with cloud models, ChatGPT/Copilot, or fully offline with Ollama/LM Studio.

**Strengths:** Safety controls, local-first option, coworker/copilot mode.
**Trade-offs:** Newer, less community data than Vault Librarian.

---

### 3. Claudesidian MCP — Claude Desktop Vault Control
**URL:** https://github.com/ProfSynapse/claudesidian-mcp
**YouTube:** https://www.youtube.com/watch?v=xBGv4RO39s0
**Why it fits:** Gives Claude agentic access to Obsidian via MCP. Team of AI assistants managing notes, projects, automation via natural language. Full vault access, note editor/reader/manager, command palette integration.

**Strengths:** MCP native, Claude Desktop integration, vault maps/templates.
**Trade-offs:** Claude-centric.

---

### 4. VaultForge — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vaultforge
**Why it fits:** Brings Claude into vault via local MCP server + in-app chat. Vault folder configured as Claude Skills directory with `SKILL.md` per skill. Auth via existing Claude Code login, no separate API key.

**Strengths:** Claude Skills progressive disclosure, live read/write/search.
**Trade-offs:** Claude-centric.

---

### 5. Smart Composer + Ollama Local AI
**YouTube:** https://www.youtube.com/watch?v=2paigpNDNz0
**Why it fits:** Ultimate local AI guide for Obsidian. Docker + Ollama with Qwen model + Smart Composer plugin for context-aware writing and vault search. Embedding model for search = librarian.

**Strengths:** 100% local, privacy-first, works with Netbird setup.
**Trade-offs:** Setup heavy.

---

### 6. AI Vault Assistant — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/ai-vault-assistant
**Why it fits:** Connects cc-switch local proxy, Obsidian vault, community plugin ecosystem, and external AI agents like Codex. Built-in Skills scan + MCP service on `127.0.0.1:33157/mcp`.

**Strengths:** Bridges external agents, plugin install/recommend, config edit with confirmation.
**Trade-offs:** Chinese docs, cc-switch dependency.

---

### 7. claude-obsidian / Claude Code + Obsidian
**URL:** https://github.com/AgriciDaniel/claude-obsidian
**Why it fits:** Local-first knowledge system for Claude Code and Agent Skills hosts. Turns sources into linked, source-cited Obsidian pages; answers from vault evidence; workflows for research, retrieval, maintenance, visual mapping.

**Strengths:** Persistent memory via markdown, no vector DB.
**Trade-offs:** Claude Code workflow.

---

### 8. kepano obsidian-skills + Obsidian CLI
**YouTube:** https://www.youtube.com/watch?v=H0MqO-2BBww
**URL:** https://github.com/kepano/obsidian-skills
**Why it fits:** Official Obsidian CLI skills. AI agent searches, reads, creates, organizes entire knowledge base from terminal. 70k cheaper than API calls.

**Strengths:** CLI-first, official, works with Claude Code.
**Trade-offs:** Requires CLI enabled.

---

### 9. Vault Doctor Agent Skill
**YouTube:** https://www.youtube.com/watch?v=We9l8WpViqc
**Why it fits:** AI skill that audits 10k-note vault — fixing broken links, inconsistent properties, outdated note types automatically. Karpathy KB workflow inspired.

**Strengths:** Maintenance-focused librarian, property normalization.
**Trade-offs:** Custom build.

---

### 10. Vault LLM Assistant — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vault-llm-assistant
**Why it fits:** Query vault with AI, get contextual answers with citations, create notes. Supports OpenAI GPT, Gemini, Claude, local LLMs LM Studio/Ollama.

**Strengths:** Simple query/create modes, citations.
**Trade-offs:** Less agentic, no skills system.

---

### 11. LLM Hub — Obsidian Plugin
**URL:** https://www.obsidianstats.com/tags/ai-assistant
**Why it fits:** Multiple AI workflows in one place. Chat with different providers, switch API/local/CLI models, vault-aware tools, prompt slash commands, reusable agent skills, RAG search, MCP server connections.

**Strengths:** Provider flexibility, workflow builder.
**Trade-offs:** UI-heavy.

---

### 12. Obsidian-SKILLS / Agent Skills Library
**URL:** https://github.com/adriangrantdotorg/Obsidian-SKILLS
**Why it fits:** Collection of Agent Skills for Obsidian. Vault Operations via CLI: read, create, append, search notes. Task & Property Management, Daily Notes.

**Strengths:** CLI-first, works with any Agent Skills host.
**Trade-offs:** Requires Obsidian CLI running.

---

### 13. Hermes Agentic Librarian Workflow
**YouTube:** https://www.youtube.com/watch?v=_bieksxg6oY
**Why it fits:** Hermes built-in LLM Wiki skill with human-in-the-loop trust layer. Bronze → Silver → Gold workflow with review inbox. Works with any agentic AI.

**Strengths:** Matches your Hermes setup, HITL verification.
**Trade-offs:** Requires Hermes.

---

### 14. obsidian-automation / PARA automation scripts
**URL:** https://github.com/mickdarling/obsidian-automation
**Why it fits:** QuickAdd scripts for PARA method. Atomization, AI-assisted categorization, automated file organization based on frontmatter, folder management.

**Strengths:** Non-AI librarian automation, fits your homelab style.
**Trade-offs:** Script maintenance.

---

### 15. Oz Orchestration Platform
**YouTube:** https://www.youtube.com/watch?v=qB_uKIB-SqQ
**Why it fits:** Cloud agents that research Obsidian vault automatically, summarize articles, create notes. Built by Warp.

**Strengths:** Scheduled research automation.
**Trade-offs:** Cloud agents, less local-first.

---

### 16. Skill and Harness Manager — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/skill-harness-manager
**Why it fits:** Consolidates AI skills, commands, agents into Obsidian ribbon/right-click. MacOS only.

**Strengths:** Unified skill launch.
**Trade-offs:** MacOS only.

---

### 17. Librarian — Book tracking plugin
**URL:** https://www.obsidianstats.com/plugins/librarian
**Why it fits:** Comprehensive book-tracking/library management. Not vault librarian, but useful if you want a reading journal.

**Strengths:** Open Library integration, reading stats.
**Trade-offs:** Different domain.

---

## Notes on Hermes Built-in
Hermes comes with `llm-wiki` skill. That's your baseline. The above plugins extend it into the vault itself.

## Recommendation for your style
Given Netbird-only, self-hosted, local-first, and Obsidian Sync $4/mo plan:
- **Primary:** Vault Librarian + Vault Operator + Claudesidian MCP. All support OpenAI-compatible local models, approval workflows, and skills.
- **Local AI stack:** Smart Composer + Ollama + Vault Doctor skill for maintenance.
- **Automation layer:** obsidian-automation scripts + QuickAdd for PARA organization.
- **Optional:** VaultForge if you want Claude Skills integration.

Want me to draft a `SKILL.md` template for your vault's librarian skill next time?
