# Ninetail-Fox Memory Engine

> **The AI Memory Exoskeleton for Indie Hackers**
> 100% local. Zero cloud dependency. Your context stays on your machine.

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-support-yellow?style=for-the-badge&logo=buy-me-a-coffee)](https://buymeacoffee.com/sunhonghua1)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

---

## 🦊 What is Ninetail-Fox?

Ninetail-Fox is an open-source **persistent memory engine** for AI coding assistants. It allows **Cursor, Claude Desktop, Windsurf**, and any MCP-compatible client to share a unified, local SQLite memory vault.

**Your AI finally remembers everything you've ever told it — across sessions, across IDEs, forever.**

### ✨ Key Features

| Feature | Description |
|---|---|
| 🧠 **Persistent Memory** | Every conversation is stored in a local SQLite vault |
| 🔍 **Hybrid Search** | BM25 keyword + Vector semantic search (4.9x compression) |
| 🌍 **Cross-Lingual** | Query in English, retrieve Chinese docs — and vice versa |
| 🔄 **Cross-IDE Sync** | Cursor ↔ Claude Desktop ↔ Windsurf share the same brain |
| 🔒 **100% Local** | Your data never leaves your machine. Period. |
| 👤 **User Profiles** | Auto-extracted facts about users for personalized context |
| ⚡ **Multi-Provider Embedding** | Google Gemini, Jina AI, DashScope — auto-fallback |

---

## 🚀 Quick Start

### 1. Clone & Install

```bash
git clone https://github.com/sunhonghua1/ninetails-memory-engine.git
cd ninetails-memory-engine

python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 2. Configure API Keys

Copy the template and add your own API keys:

```bash
cp engine/embedding_config.json engine/embedding_config.local.json
```

Edit `engine/embedding_config.local.json` with your real keys:
- **Google Gemini**: [Get free API key](https://aistudio.google.com/apikey)
- **Jina AI**: [Get free API key](https://jina.ai/embeddings/)

### 3. Connect to Cursor

Add this to your `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "ninetail-fox-memory": {
      "command": "/path/to/your/.venv/bin/python",
      "args": ["/path/to/engine/mcp_memory_server.py"],
      "env": {
        "MEMORY_STORAGE_PATH": "/Users/YOU/.ninetail-fox/memory.sqlite"
      }
    }
  }
}
```

### 4. Connect to Claude Desktop

Add the same config block to `~/Library/Application Support/Claude/claude_desktop_config.json`.

**That's it.** Both IDEs now share the same memory vault. 🎉

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────┐
│           MCP Protocol (stdio)              │
├───────────┬───────────┬─────────────────────┤
│  Cursor   │  Claude   │  Windsurf / Others  │
└─────┬─────┴─────┬─────┴──────────┬──────────┘
      │           │                │
      ▼           ▼                ▼
┌─────────────────────────────────────────────┐
│       mcp_memory_server.py (MCP Host)       │
├─────────────────────────────────────────────┤
│  Tools: search_memory, add_memory,          │
│         get_user_profile, list_users,       │
│         add_user_fact, extract_facts        │
└──────────────────┬──────────────────────────┘
                   │
      ┌────────────┼────────────┐
      ▼            ▼            ▼
┌──────────┐ ┌──────────┐ ┌──────────────┐
│ Memory   │ │ Profile  │ │  Embedding   │
│ Core     │ │ Manager  │ │  Provider    │
│ (v4.5)   │ │ (SQLite) │ │  (Multi-API) │
└──────────┘ └──────────┘ └──────────────┘
      │            │
      ▼            ▼
   ~/.ninetail-fox/
   ├── conversations.sqlite   (memory vault)
   ├── profiles.sqlite        (user facts)
   └── vector_cache.sqlite    (embedding cache)
```

---

## 📂 Engine Files

| File | Purpose |
|---|---|
| `mcp_memory_server.py` | MCP server — connects to Cursor/Claude/Windsurf |
| `openclaw_memory_v4.py` | Core memory engine — hybrid BM25+Vector search |
| `embedding_provider.py` | Multi-provider embedding (Google/Jina/DashScope) |
| `user_profile_manager.py` | SQLite-based user fact storage |
| `fact_extractor.py` | Auto-extract structured facts from conversations |
| `embedding_config.json` | API key configuration template |

---

## 🎬 Live Demo

Watch the engine in action — same memory vault, two different AI clients:

**Cursor** asks: *"How is our system approval process designed?"*
→ Engine returns the exact dual-gate architecture with VETO rules.

**Claude Desktop** asks: *"Search the vault for the VETO rule."*
→ Same results, retrieved from the same local SQLite vault. Seamless.

---

## ☕ Support This Project

If Ninetail-Fox saves you time and makes your AI workflow better, consider buying me a coffee:

<a href="https://buymeacoffee.com/sunhonghua1">
  <img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=☕&slug=sunhonghua1&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" />
</a>

---

## 📄 License

MIT License — Use it, fork it, build on it. Just remember where the fox came from. 🦊
