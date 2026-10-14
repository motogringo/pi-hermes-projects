# Obsidian Vault Librarian Skills & Tools — Ranked Findings

Compiled for Moto Gringo Productions / personal vault style. Focus: agentic librarian / vault management, local-first, skills-based, and automation-friendly.

## Ranking Criteria
1. **Local-first / self-hosted fit** — Netbird-only, no cloud lock-in
2. **Agent/Skills model** — Agent Skills / SKILL.md compatible
3. **MOC / link hygiene** — Maps of Content, wikilink repair, orphan detection
4. **Vault operations** — read/search/write with approval
5. **Hermes portable** — can run as Hermes skill, not Obsidian plugin UI

---

### 1. Hermes Agentic Librarian Workflow
**YouTube:** https://www.youtube.com/watch?v=_bieksxg6oY
**Why it fits:** Native Hermes. LLM Wiki skill + Bronze→Silver→Gold + HITL review inbox. MOC building, link hygiene, human approval. Exactly your stack.

**Strengths:** Hermes-native, HITL trust layer, no PARA.
**Trade-offs:** Requires Hermes setup.

---

### 2. Vault Doctor Agent Skill
**YouTube:** https://www.youtube.com/watch?v=We9l8WpViqc
**Why it fits:** AI skill that audits vault — fixes broken links, inconsistent properties, outdated note types. Karpathy KB workflow. Perfect for MOC maintenance.

**Strengths:** Maintenance-focused librarian, property normalization.
**Trade-offs:** Custom build.

---

### 3. kepano obsidian-skills + Obsidian CLI
**YouTube:** https://www.youtube.com/watch?v=H0MqO-2BBww
**URL:** https://github.com/kepano/obsidian-skills
**Why it fits:** Official Obsidian CLI skills. Agent Skills format. Search, read, create, organize. Portable to Hermes. MOC building via CLI.

**Strengths:** CLI-first, official, Hermes portable.
**Trade-offs:** Requires CLI enabled.

---

### 4. Obsidian-SKILLS / Agent Skills Library
**URL:** https://github.com/adriangrantdotorg/Obsidian-SKILLS
**Why it fits:** Collection of Agent Skills. Vault Operations via CLI, Task & Property Management, Daily Notes. No PARA.

**Strengths:** Agent Skills format, Hermes portable.
**Trade-offs:** Requires Obsidian CLI.

---

### 5. Vault Librarian — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vault-librarian
**Why it fits:** Agent living in Obsidian. Skills via `.agents/skills/<name>/SKILL.md`. Plain-language search, approval workflow. MOC support.

**Strengths:** Skills system, mobile parity.
**Trade-offs:** Obsidian plugin UI, not Hermes native.

---

### 6. Vault Operator — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vault-operator
**Why it fits:** Agentic AI operating layer. Plans, searches, reads, writes, reports. Approval, undo. BYOK + MCP. MOC building.

**Strengths:** Safety controls, local-first option.
**Trade-offs:** Obsidian plugin.

---

### 7. VaultForge — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vaultforge
**Why it fits:** Claude Skills directory with `SKILL.md` per skill. Live read/write/search. MOC support.

**Strengths:** Claude Skills progressive disclosure.
**Trade-offs:** Claude-centric, plugin UI.

---

### 8. AI Vault Assistant — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/ai-vault-assistant
**Why it fits:** Connects local proxy, vault, external agents. Built-in Skills scan + MCP. MOC building possible.

**Strengths:** Bridges external agents.
**Trade-offs:** Obsidian plugin, cc-switch dependency.

---

### 9. claude-obsidian / Claude Code + Obsidian
**URL:** https://github.com/AgriciDaniel/claude-obsidian
**Why it fits:** Local-first knowledge system. Turns sources into linked, source-cited pages. MOCs, Maps of Content, Canvas views.

**Strengths:** Persistent memory via markdown.
**Trade-offs:** Claude Code workflow.

---

### 10. Claudesidian MCP — Claude Desktop Vault Control
**YouTube:** https://www.youtube.com/watch?v=xBGv4RO39s0
**URL:** https://github.com/ProfSynapse/claudesidian-mcp
**Why it fits:** MCP server for Claude Desktop to manage Obsidian vault. Note editor/reader/manager, vault maps/templates.

**Strengths:** MCP native.
**Trade-offs:** Claude-centric.

---

### 11. Smart Composer + Ollama Local AI
**YouTube:** https://www.youtube.com/watch?v=2paigpNDNz0
**Why it fits:** Local AI stack for vault search and writing. Embedding model = librarian. MOC building via Smart Composer.

**Strengths:** 100% local, privacy-first.
**Trade-offs:** Setup heavy.

---

### 12. Vault LLM Assistant — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/vault-llm-assistant
**Why it fits:** Query vault with AI, citations, create notes. MOC building possible.

**Strengths:** Simple query/create.
**Trade-offs:** Less agentic.

---

### 13. LLM Hub — Obsidian Plugin
**URL:** https://www.obsidianstats.com/tags/ai-assistant
**Why it fits:** Multi-provider chat, vault-aware tools, reusable agent skills, RAG search. MOC support.

**Strengths:** Provider flexibility.
**Trade-offs:** UI-heavy, plugin.

---

### 14. Oz Orchestration Platform
**YouTube:** https://www.youtube.com/watch?v=qB_uKIB-SqQ
**Why it fits:** Cloud agents research vault automatically, summarize, create notes. MOC building possible.

**Strengths:** Scheduled research.
**Trade-offs:** Cloud, less local-first.

---

### 15. Skill and Harness Manager — Obsidian Plugin
**URL:** https://community.obsidian.md/plugins/skill-harness-manager
**Why it fits:** Consolidates AI skills. MOC support via skills.

**Strengths:** Unified skill launch.
**Trade-offs:** MacOS only, plugin.

---

### 16. Librarian — Book tracking plugin
**URL:** https://www.obsidianstats.com/plugins/librarian
**Why it fits:** Library management, not vault librarian.

**Strengths:** Open Library integration.
**Trade-offs:** Different domain.

---

## Dropped
obsidian-automation / PARA scripts — removed per your request.

## Recommendation for your style
Hermes-native + MOC-centric, no PARA:
- **Primary:** Hermes Agentic Librarian Workflow + Vault Doctor Agent Skill
- **Portable skills:** kepano obsidian-skills + Obsidian-SKILLS
- **Local AI:** Smart Composer + Ollama
- **Optional Obsidian plugins:** Vault Librarian / Vault Operator if you want in-app UI

Want a Hermes `vault-librarian` SKILL.md draft now?
