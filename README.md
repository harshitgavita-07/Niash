# Niash

**Human–AI shared control for your computer.**

[Issues](https://github.com/harshitgavita-07/Niash/issues) · [Development](#development) · [Testing](#testing)

## What is Niash?

Niash is a shared-control layer that lets humans and AI work on the same computer at the same time.

Today, when you give an AI a task, it takes control of your computer — you wait. Niash changes this: the human keeps working while the AI works alongside them, with built-in priority when physical interaction conflicts arise.

## The Problem

```
Current model:
  Human gives AI a task → AI takes control → Human waits → AI finishes

Niash model:
  Human works  ↕  AI works  ↕  Shared computer
```

When AI needs to use your keyboard, mouse, or screen, Niash mediates access — giving you priority when you're physically interacting, and letting background tasks continue when you're not.

## Core Idea

> Humans and AI should be able to work on the same computer at the same time.

Niash builds on an existing agent/desktop execution foundation to add:

- **Human presence awareness** — detect when you're actively using the computer
- **Shared resource arbitration** — coordinate terminal, file, and application access
- **Human priority** — yield to physical input automatically
- **Background task continuity** — AI works while you work
- **Safe interruption** — pause and resume without data loss
- **Verification** — review actions before they execute

## Architecture

```
Human
   ↕
Niash shared-control layer
   ↕
AI agents
   ↕
Computer
```

**Human presence** — tracks mouse/keyboard activity to detect when the human is actively using the computer.

**Computer context** — accesses filesystem, terminal, browser, and application state.

**Interaction arbitration** — coordinates concurrent access between human and AI agents.

**Background agent tasks** — runs AI work in the background without blocking the human.

**Physical vs non-physical actions** — distinguishes between actions that need physical input (typing, clicking) and those that don't (file writes, API calls).

**Verification** — reviews and approves actions before execution.

**Safety/governance** — enforces permissions, workspace scoping, and approval gates.

## Current Status

### Complete

- Agent runtime with multi-turn conversation and tool calling
- 25+ connectors (GitHub, Slack, Jira, Gmail, Google Calendar, Notion, etc.)
- MCP (Model Context Protocol) support for external tool servers
- Auto-approve reviewer for safety
- Voice input (local Whisper transcription)
- Desktop app (Tauri shell with system tray, auto-update)
- Scheduled automations (cron-based)
- Memory system (persistent across sessions)
- Multi-agent teams with board and chat
- Persona system (configurable coworker personalities)

### In Progress

- Human activity awareness
- Shared resource arbitration
- Background task coexistence

### Planned

- Advanced cursor intelligence
- Reaction engine
- Agent swarm coordination
- Enhanced memory architecture
- Cross-platform optimization

## MVP

The first MVP delivers: **a human can continue working while an AI task runs in the background, and when AI needs physical computer interaction, Niash mediates access with human priority.**

## Why Niash?

Most AI tools follow a turn-based model: you ask, it works, you wait. This breaks down when:

- You need to keep working while AI handles a task
- AI and human need to use the same resources simultaneously
- Background tasks should continue without blocking interaction

Niash solves this by treating the computer as a shared workspace rather than a exclusive lock.

## Development

### Prerequisites

- Python 3.10+
- Node.js 20+
- Rust toolchain (via [rustup](https://rustup.rs/)) — for desktop shell

### Setup

```bash
git clone https://github.com/harshitgavita-07/Niash
cd Niash

# One-time bootstrap — creates Python venv at .venv
bash packaging/setup_dev_env.sh

# Start the local agent server
.venv/bin/niash-server --cwd ~/some/project --port 8765
# Windows: .venv\Scripts\niash-server.exe

# In a second terminal, start the GUI
cd surfaces/gui
npm install
npm run dev        # browser UI on Vite dev port
```

### Desktop App

For the full desktop app instead of browser UI:

```bash
cd surfaces/gui
npm run tauri dev   # Tauri shell launches window + server
```

### Run from Source

The standalone server creates a per-launch token at `<state-dir>/sidecar-8765.token`. For direct API calls, send its value in the `X-Niash-Token` header.

## Testing

### Backend Tests

```bash
# From project root
pytest tests/ -q

# Specific test file
pytest tests/test_engine.py -q
```

### GUI Unit Tests

```bash
cd surfaces/gui
npm test
```

### GUI E2E Tests

```bash
cd surfaces/gui
npm run e2e
```

### Current Baseline

- Backend: ~111 passed, ~6 failed (environment-specific: Windows `time.tzset`, MCP path issues)
- GUI: Tests available but require Playwright setup

## Repository Layout

| Directory | What's in it |
|---|---|
| `coworker/` | Python backend — agent engine, providers, connectors, MCP, memory, automations |
| `surfaces/gui/` | Desktop app — React UI + Tauri shell |
| `stt/` | Speech-to-text sidecar (Rust) |
| `packaging/` | Installer builds, auto-update, dev bootstrap |
| `docs/` | Design specs, audit, baseline docs |
| `tests/` | Backend test suite |
| `scripts/` | Corpus building, reviewer evaluation |

## Roadmap

1. **Shared interaction MVP** — human and AI work concurrently
2. **Background task coexistence** — AI tasks run without blocking
3. **Context-aware interaction** — AI adapts to human presence
4. **Better human/AI coordination** — seamless handoff
5. **Persistent workflows** — long-running background tasks
6. **Cross-platform support** — optimized for each OS

## License

MIT — see [LICENSE](LICENSE).

Niash builds on an existing agent/desktop execution foundation. See [docs/NIASH_BASELINE.md](docs/NIASH_BASELINE.md) for architecture details and attribution.
