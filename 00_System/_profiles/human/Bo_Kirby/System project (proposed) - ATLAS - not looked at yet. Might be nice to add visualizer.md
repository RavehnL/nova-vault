## Component Lexicon

### 🧠 The Sovereign (Human)

The ultimate authority. All loops begin and end with human intent. The system exists to extend cognitive leverage, not replace human judgment.

### ⚙️ Hermes (The Agentic Core)

The orchestrator. It operates on an OODA loop (Observe, Orient, Decide, Act). It translates human intent into tool calls (MCP), manages the context window by pulling from memory, and executes multi-step workflows.

### 📒 Obsidian Vault (Semantic Memory)

The long-term, human-readable truth. Git-backed for version control. This is the "Cookbook"—the definitive record of projects, knowledge, and daily logs. Both the Human and Hermes write here.

### 🧠 LanceDB (Episodic Memory)

The machine-readable, vectorized memory. This is the "Pantry"—where the raw ingredients of past conversations and document chunks are stored for rapid semantic retrieval (`/search`).

### 🔥 Ollama (Local Inference)

The compute engine. Split into two isolated services:

- **:11435 (LLM):** The reasoning engine (Gemma2/GLM4). The "Stove" where the actual cooking happens.
- **:11436 (Embeddings):** The meaning extractor (Nomic). Turns text into vector coordinates so they can be stored in the Pantry.

### 📚 Open Notebook (Deep Synthesis)

The prep kitchen. When the ingredients (PDFs, repos) are too large for a simple chat, Open Notebook chunks them, runs them through the Embedding service, synthesizes them via the LLM, and can generate audio briefings via Kokoro.

### 🔊 Kokoro TTS (Voice)

The local voice. Allows the system to communicate audibly without relying on cloud APIs. Enables "eyes-free" consumption of synthesized research.

### 🖥️ NovaHub (Control Surface)

The dashboard. A Next.js web UI that monitors the health of all local services, displays agent statuses, and visualizes system resources (CPU/RAM/VRAM). The "Kitchen Display System."


I see exactly what's happening. You pasted the code into VSCodium, but it's showing the raw text instead of rendering the visual diagram.

Here is how we fix this right now, plus an immediate visual map you can look at without any special software.

### 1. The Instant Visual Map (ASCII Architecture)

Here is the map in plain text. You can read this immediately to understand how the data flows from you, through the agent, into the models, and back to memory.

text

========================================================================

🧠 THE SOVEREIGN (Human Intent)

========================================================================

| |

v v

[📓 Obsidian Vault] [🖥️ NovaHub Dashboard]

(Read/Write Daily Notes) (Monitor System Health)

| |

+------------------+---------------+

|

v

========================================================================

⚙️ HERMES (The Agentic Core / Chef)

========================================================================

| | | |

| (MCP) | (Search) | (API Call) | (Trigger)

v v v v

[📂 Vault] [🧠 LanceDB] [🔥 Ollama] [📚 Open Notebook]

Operations Episodic Local Inference Deep RAG Synthesis

| | | |

| | +--------+-------+

| | |

| | v

| | ===================================

| | ⚙️ LOCAL COMPUTE (No Cloud / The Stove)

| | ===================================

| | [🔥 LLM :11435] [🧊 Embed :11436]

| | (Gemma2 / GLM4) (Nomic-Embed)

| | [🔊 Kokoro TTS :8880]

| | |

+------------+---------------+

|

v

========================================================================

💾 SOVEREIGN MEMORY (The Pantry & Cookbook)

========================================================================

📂 Semantic: ~/nova-vault (Git-Backed Markdown)

🧠 Episodic: ~/.hermes/lancedb (Vector Embeddings)

---

### 2. How to view the beautiful Mermaid diagram you just pasted

The code you pasted uses "Mermaid," a language that turns text into flowcharts. VSCodium doesn't render it automatically; you have to turn on preview mode.

**To see it in VSCodium:**

1. Make sure the file is saved as a Markdown file (e.g., `Nova_System_Map.md`).
2. Install the extension: Go to the Extensions tab (square icon on the left), search for **"Markdown Preview Mermaid Support"** and install it.
3. Open the preview pane: Press `Ctrl + Shift + V` (or click the "Open Preview to the Side" icon in the top right of the editor). The raw code will magically transform into a high-definition flowchart.

**To see it in 2 seconds on the web:**

1. Open your browser and go to **[mermaid.live](https://mermaid.live)**.
2. Delete the default code on the left side of the screen.
3. Paste the code block I gave you earlier (starting from `graph TD` down to the final `}`).
4. The visual diagram will instantly appear on the right side. You can even download it as a PNG image to keep on your desktop.

---

### 3. How to view it in Obsidian (Where it truly belongs)

Since we are building the "Living File" architecture in Obsidian, this map will live best there.

1. Open your Nova Vault in Obsidian.
2. Create a new note: `00_System/Nova_Architecture.md`.
3. Paste the Mermaid code block into that note.
4. Obsidian natively supports Mermaid. Just click out of editing mode (press `Ctrl+E` to toggle reading view), and the diagram will render perfectly inside your vault.

**The takeaway:** You are the Sovereign at the top. Hermes is the middleman executing your will. Ollama is the engine doing the heavy lifting. Obsidian and LanceDB are the memory banks where the work is stored. Everything stays inside the box; nothing phones home.