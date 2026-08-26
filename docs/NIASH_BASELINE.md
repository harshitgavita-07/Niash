# Niash Baseline

## Starting Repository

Niash is initialized from the OpenWorker codebase (https://github.com/andrewyng/openworker), an open-source AI coworker platform.

## Current Architecture

### Backend (Python)
- **coworker/** — Core engine: agent runtime, model providers, connectors, MCP client, memory, automations
  - `engine.py` — Main agent loop with tool calling, approval gating, and auto-approve reviewer
  - `providers/` — LLM providers: OpenAI, Anthropic, Google Gemini, Vertex, Bedrock, and more
  - `connectors/` — 25+ integrations: GitHub, Slack, Jira, Gmail, Google Calendar, Notion, etc.
  - `mcp/` — MCP client with stdio and streamable-HTTP transport, OAuth support
  - `server/` — FastAPI sidecar serving the GUI, WebSocket events, REST API
  - `teams/` — Board/journal for agent teams, multi-coworker sessions
  - `personas/` — Coworker personality system with builtin personas and skills

### Desktop Shell (Rust/Tauri)
- **surfaces/gui/src-tauri/** — Tauri 2.x native shell
  - Manages Python server sidecar lifecycle
  - System tray with close-to-tray
  - Voice input (speech-to-text via Whisper)
  - Auto-update via tauri-plugin-updater

### Frontend (React/TypeScript)
- **surfaces/gui/src/** — React SPA
  - Session management, transcript, composer
  - Settings, personas, integrations
  - Board overlay for agent teams
  - Onboarding wizard

### Speech-to-Text
- **stt/** — Rust crate for local Whisper-based transcription

### Packaging
- **packaging/** — macOS DMG, Windows NSIS/MSI installers, dev bootstrap scripts

## Functionality Already Exists

1. **Agent Runtime** — Multi-turn conversation with tool calling, context management, compaction
2. **25+ Connectors** — GitHub, Slack, Jira, Gmail, Google Calendar, Notion, Linear, HubSpot, etc.
3. **MCP Support** — Model Context Protocol for external tool servers
4. **Auto-Approve Reviewer** — Safety gate that judges proposed actions
5. **Voice Input** — Local Whisper transcription
6. **Desktop App** — Tauri shell with system tray, auto-update
7. **Scheduled Automations** — Cron-based recurring tasks
8. **Memory System** — Persistent agent memory across sessions
9. **Multi-Coworker Teams** — Board, team chat, shared workspaces
10. **Persona System** — Configurable coworker personalities with skills

## What Has Been Renamed/Rebranded

All user-facing references to "OpenWorker" have been changed to "Niash":
- README.md title and descriptions
- Package display name (pyproject.toml)
- Desktop app name (tauri.conf.json, Info.plist, lib.rs)
- GUI brand wordmark, splash screen, onboarding
- Server HTML responses
- OAuth client name
- All user-facing strings in components

## What Has NOT Been Changed

- Internal Python module names (`coworker/` package)
- CLI entry points (`openworker`, `openworker-server`, `ocw`)
- Import paths and class names
- API token header name (`X-OpenWorker-Token`) — backward compatibility
- localStorage keys — existing user data preserved
- Internal variable/function names (`onOpenWorker` callbacks)
- Test infrastructure and test logic
- Architecture and code structure
