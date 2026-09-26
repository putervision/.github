# 🚀 Getting Started with the PuterVision Cognitive Pentad

This guide covers installing, configuring, and orchestrating the PuterVision MCP Pentad across your preferred AI coding environments and agent runtimes.

---

## 1. Quick Install: Global CLI

Install all 5 Pentad servers globally using `npm`:

```bash
npm install -g \
  @putervision/state-memory-mcp \
  @putervision/vision-memory-mcp \
  @putervision/world-model-mcp \
  @putervision/agent-reasoning-mcp \
  @putervision/behavior-mcp
```

### Initializing a Project

From your target project repository root, run the initialization commands to create local SQLite databases in WAL mode and scaffold IDE instruction contracts:

```bash
state-memory-mcp init
vision-memory-mcp init
world-model-mcp init
agent-reasoning-mcp init
behavior-mcp init
```

Each initialization command:
1. Registers your project directory in the global registry (`~/.<server>/projects.json`).
2. Creates isolated local storage directories (e.g. `.state-memory-mcp/`, `.world-model-mcp/`).
3. Scaffolds instruction contracts in `.agents/AGENTS.md`, `CLAUDE.md`, and `.windsurfrules`.
4. Merges MCP server configs into `.cursor/mcp.json` and `.vscode/mcp.json`.

---

## 2. Environment Variables

Configure your shell profile (e.g. `~/.bashrc`, `~/.zshrc`) or `.env` file:

| Variable | Default | Purpose |
| :--- | :---: | :--- |
| `PENTAD_HMAC_SECRET` | *(required)* | 32+ byte secret shared between `agent-reasoning-mcp` and `behavior-mcp` for cryptographic intention token signing. |
| `OFFLINE` | `0` | Set to `1` to enforce strict air-gapped execution (disables any external model downloads). |
| `SKIP_MODEL_LOAD` | `0` | Set to `1` to bypass local ONNX/CLIP loading and operate exclusively on L1/L2 fast heuristics and perceptual hashing. |
| `REASONING_LOG_LEVEL`| `info` | Logging verbosity (`debug`, `info`, `warn`, `error`). |
| `STATE_MEMORY_MCP_DIR` | local | Custom directory path for SQLite databases. |

---

## 3. Client Configuration Templates

### A. Claude Code (`~/.claude.json` or project `.claude.json`)

```json
{
  "mcpServers": {
    "state-memory-mcp": {
      "command": "npx",
      "args": ["-y", "@putervision/state-memory-mcp"]
    },
    "vision-memory-mcp": {
      "command": "npx",
      "args": ["-y", "@putervision/vision-memory-mcp"]
    },
    "world-model-mcp": {
      "command": "npx",
      "args": ["-y", "@putervision/world-model-mcp"]
    },
    "agent-reasoning-mcp": {
      "command": "npx",
      "args": ["-y", "@putervision/agent-reasoning-mcp"],
      "env": {
        "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here"
      }
    },
    "behavior-mcp": {
      "command": "npx",
      "args": ["-y", "@putervision/behavior-mcp"],
      "env": {
        "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here"
      }
    }
  }
}
```

### B. Cursor (`.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "state-memory-mcp": { "command": "state-memory-mcp" },
    "vision-memory-mcp": { "command": "vision-memory-mcp" },
    "world-model-mcp": { "command": "world-model-mcp" },
    "agent-reasoning-mcp": {
      "command": "agent-reasoning-mcp",
      "env": { "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here" }
    },
    "behavior-mcp": {
      "command": "behavior-mcp",
      "env": { "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here" }
    }
  }
}
```

### C. Windsurf (`mcp_config.json`)

```json
{
  "mcpServers": {
    "state-memory-mcp": { "command": "state-memory-mcp" },
    "vision-memory-mcp": { "command": "vision-memory-mcp" },
    "world-model-mcp": { "command": "world-model-mcp" },
    "agent-reasoning-mcp": {
      "command": "agent-reasoning-mcp",
      "env": { "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here" }
    },
    "behavior-mcp": {
      "command": "behavior-mcp",
      "env": { "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here" }
    }
  }
}
```

### D. Google Antigravity / Gemini CLI (`~/.gemini/antigravity/mcp_config.json`)

```json
{
  "mcpServers": {
    "state-memory-mcp": { "command": "state-memory-mcp" },
    "vision-memory-mcp": { "command": "vision-memory-mcp" },
    "world-model-mcp": { "command": "world-model-mcp" },
    "agent-reasoning-mcp": {
      "command": "agent-reasoning-mcp",
      "env": { "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here" }
    },
    "behavior-mcp": {
      "command": "behavior-mcp",
      "env": { "PENTAD_HMAC_SECRET": "your-secure-32-byte-secret-key-here" }
    }
  }
}
```

---

## 4. Diagnostics & Health Verification

Each Pentad server provides built-in CLI diagnostic tools to verify database integrity, journal mode (WAL), and cryptographic hash chains:

```bash
# Run health diagnostics across servers
state-memory-mcp doctor
world-model-mcp doctor
agent-reasoning-mcp doctor
behavior-mcp doctor

# Audit cryptographic SHA-256 Merkle event ledgers
state-memory-mcp audit
agent-reasoning-mcp audit
behavior-mcp audit
```

Expected diagnostic output:
```
✔ SQLite database accessibility: OK
✔ Journal mode: "wal"
✔ Database integrity: "ok"
✔ Event chain verification: VALID (unbroken)
Doctor diagnostic check PASSED.
```

---

## 5. Visual Web Visualizers

Each server includes interactive web viewers for inspecting local databases in your browser:

```bash
# Open interactive 3D state graph
state-memory-mcp view

# Inspect spatial entities in 3D scene
world-model-mcp view

# View reasoning goal DAGs and decision traces
agent-reasoning-mcp view
```

---

## 🔗 Related Documentation

- [**PuterVision Organization README**](https://github.com/putervision/.github/blob/main/profile/README.md)
- [**68-Tool Model Context Protocol Reference (`TOOLS.md`)**](https://github.com/putervision/.github/blob/main/profile/TOOLS.md)
- [**System One Architecture Deep Dive (`ARCHITECTURE.md`)**](https://github.com/putervision/.github/blob/main/profile/ARCHITECTURE.md)
