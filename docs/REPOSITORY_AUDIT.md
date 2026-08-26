# Niash Repository Audit

Generated: 2026-08-27

## Top-Level Directories

| Directory | Classification | Notes |
|-----------|---------------|-------|
| `.claude/` | DEVELOPMENT | Claude Code agent configuration, local to user |
| `.github/` | REQUIRED | CI workflows (release.yml) |
| `.gitignore` | REQUIRED | Git ignore rules |
| `config/` | GENERATED | Generated config files (hypercorn.toml, secret_key, logs). Already in .gitignore |
| `coworker/` | REQUIRED | Core Python backend — agent engine, providers, connectors, MCP, server |
| `docs/` | DOCUMENTATION | Design specs, baseline docs, assets |
| `packaging/` | USED BY BUILD | Installer builds (DMG, Windows), PyInstaller spec, dev bootstrap |
| `reports/` | DOCUMENTATION | Reviewer evaluation reports (historical reference) |
| `scripts/` | USED BY TESTS | Corpus building, reviewer evaluation, validation scripts |
| `stt/` | REQUIRED | Speech-to-text sidecar (Rust/Whisper) |
| `surfaces/` | REQUIRED | Desktop app — React GUI + Tauri shell |
| `tests/` | USED BY TESTS | Backend test suite (136+ test files) |
| `ui-mocks/` | OPTIONAL | UI mockup HTML files — design reference, not used by runtime or tests |

## Root Files

| File | Classification | Notes |
|------|---------------|-------|
| `.gitignore` | REQUIRED | Git ignore rules |
| `CLAUDE.md` | DOCUMENTATION | AWS Agent Toolkit rules for Claude Code |
| `LICENSE` | REQUIRED | MIT License (OpenWorker origin) |
| `README.md` | REQUIRED | Product documentation — needs rewrite for Niash |
| `pyproject.toml` | REQUIRED | Python package configuration |

## coworker/ (Core Backend)

| Subdirectory | Classification | Notes |
|-------------|---------------|-------|
| `coworker/__init__.py` | REQUIRED | Package init |
| `coworker/agent.py` | REQUIRED | Agent base |
| `coworker/agents/` | REQUIRED | Agent implementations |
| `coworker/attachments.py` | REQUIRED | File attachment handling |
| `coworker/audit.py` | REQUIRED | Audit logging |
| `coworker/automation/` | REQUIRED | Scheduled task automation |
| `coworker/catalog.py` | REQUIRED | Skill catalog |
| `coworker/cli.py` | REQUIRED | CLI entry point |
| `coworker/cloud.py` | USED BY RUNTIME | Cloud sign-in and managed connectors |
| `coworker/compaction.py` | REQUIRED | Context compaction |
| `coworker/config.py` | REQUIRED | Configuration management |
| `coworker/connections.py` | REQUIRED | Connection management |
| `coworker/connectors/` | REQUIRED | 25+ integrations (GitHub, Slack, Jira, etc.) |
| `coworker/connectors/experimental/` | OPTIONAL | Experimental connectors |
| `coworker/conversations.py` | REQUIRED | Conversation management |
| `coworker/engine.py` | REQUIRED | Main agent loop with tool calling |
| `coworker/environment.py` | REQUIRED | Environment detection |
| `coworker/events.py` | REQUIRED | Event system |
| `coworker/inbox.py` | REQUIRED | Inbox system |
| `coworker/inbox_routing.py` | REQUIRED | Inbox routing |
| `coworker/interactions.py` | REQUIRED | User interactions |
| `coworker/mcp/` | REQUIRED | MCP client (stdio + streamable-HTTP) |
| `coworker/memory/` | REQUIRED | Persistent agent memory |
| `coworker/mentions.py` | REQUIRED | Slack mention routing |
| `coworker/overrides.py` | REQUIRED | Override system |
| `coworker/pdf_support.py` | REQUIRED | PDF attachment handling |
| `coworker/permissions.py` | REQUIRED | Permission system |
| `coworker/personas/` | REQUIRED | Coworker personality system |
| `coworker/personas/builtin/` | REQUIRED | Built-in persona definitions |
| `coworker/project.py` | REQUIRED | Project management |
| `coworker/projects.py` | REQUIRED | Project management |
| `coworker/provenance.py` | REQUIRED | Action provenance tracking |
| `coworker/providers/` | REQUIRED | LLM providers (OpenAI, Anthropic, Google, etc.) |
| `coworker/readonly.py` | REQUIRED | Read-only scoping |
| `coworker/reviewer.py` | REQUIRED | Auto-approve safety reviewer |
| `coworker/risk.py` | REQUIRED | Risk assessment |
| `coworker/roots.py` | REQUIRED | Workspace root management |
| `coworker/secrets.py` | REQUIRED | Secret store |
| `coworker/selfwake.py` | REQUIRED | Self-wake system |
| `coworker/server/` | REQUIRED | FastAPI sidecar server |
| `coworker/session_facts.py` | REQUIRED | Session facts |
| `coworker/sessions.py` | REQUIRED | Session management |
| `coworker/skills/` | REQUIRED | Skills system |
| `coworker/subscriptions.py` | REQUIRED | Subscription management |
| `coworker/teams/` | REQUIRED | Board/journal for agent teams |
| `coworker/testing/` | USED BY TESTS | Test helpers (FakeSlack) |
| `coworker/toolchain.py` | REQUIRED | Tool chain management |
| `coworker/tools/` | REQUIRED | Tool implementations |
| `coworker/tui/` | USED BY RUNTIME | Terminal UI (Textual) |
| `coworker/unattended.py` | REQUIRED | Unattended mode |
| `coworker/unrouted.py` | REQUIRED | Unrouted messages |
| `coworker/web/` | REQUIRED | Web guard for URL security |
| `coworker/workspace_trust.py` | REQUIRED | Workspace trust system |

## surfaces/gui/ (Desktop App)

| Subdirectory | Classification | Notes |
|-------------|---------------|-------|
| `surfaces/gui/assets/` | USED BY BUILD | App icon |
| `surfaces/gui/e2e/` | USED BY TESTS | Playwright E2E tests (80+ spec files) |
| `surfaces/gui/e2e-live/` | USED BY TESTS | Live E2E tests against real server |
| `surfaces/gui/src/` | REQUIRED | React TypeScript source |
| `surfaces/gui/src/components/` | REQUIRED | UI components (50+ files) |
| `surfaces/gui/src/components/connectors/` | REQUIRED | Connector-specific UI |
| `surfaces/gui/src/connectors/` | REQUIRED | Connector logic |
| `surfaces/gui/src/fonts/` | REQUIRED | Font assets |
| `surfaces/gui/src/providers/` | REQUIRED | Provider logos |
| `surfaces/gui/src-tauri/` | REQUIRED | Tauri 2.x native shell |
| `surfaces/gui/src-tauri/src/` | REQUIRED | Rust source (lib.rs) |
| `surfaces/gui/src-tauri/icons/` | REQUIRED | App icons |
| `surfaces/gui/src-tauri/capabilities/` | REQUIRED | Tauri capabilities |

## tests/

| Classification | Notes |
|---------------|-------|
| `tests/test_*.py` | Backend test files (136 files) |
| `tests/corpora/` | Test corpora (JSONL files for reviewer eval) |
| `tests/conftest.py` | pytest configuration |

## reports/

| Classification | Notes |
|---------------|-------|
| `reports/reviewer-eval-*.md` | Historical reviewer evaluation results |

## ui-mocks/

| Classification | Notes |
|---------------|-------|
| `ui-mocks/*.html` | Static HTML mockups for UI design. Not used by runtime or tests. |

## Generated Artifacts (Not Tracked)

| Artifact | Location | Status |
|----------|----------|--------|
| `__pycache__/` | Throughout coworker/, scripts/ | In .gitignore |
| `*.pyc` | Throughout | In .gitignore |
| `*.egg-info/` | coworker.egg-info/ | In .gitignore |
| `.pytest_cache/` | Root | In .gitignore |
| `config/` | Root | In .gitignore |
| `node_modules/` | surfaces/gui/ | In .gitignore |
| `.venv/` | Root | In .gitignore |

## Proposed Deletions

### SAFE TO REMOVE

| Path | Reason | Evidence |
|------|--------|----------|
| `ui-mocks/connectors-redesign.html` | Design mockup, not used by runtime/tests | Static HTML, no imports, no test references |
| `ui-mocks/redesign.html` | Design mockup, not used by runtime/tests | Static HTML, no imports, no test references |
| `ui-mocks/voice-input-composer-states.html` | Design mockup, not used by runtime/tests | Static HTML, no imports, no test references |
| `ui-mocks/voice-input-settings.html` | Design mockup, not used by runtime/tests | Static HTML, no imports, no test references |
| `coworker.egg-info/` | Generated build artifact | In .gitignore, should not be tracked |
| `.pytest_cache/` | Generated test cache | In .gitignore, should not be tracked |

### KEEP

| Path | Reason |
|------|--------|
| `reports/` | Historical evaluation data, valuable reference |
| `packaging/openworker-server.spec` | PyInstaller spec needed for desktop builds |
| `packaging/server_entry.py` | PyInstaller entry point needed for desktop builds |
| `scripts/` | Corpus building and evaluation tools |
| `CLAUDE.md` | AWS Agent Toolkit rules |
| `docs/assets/how-it-works.png` | Architecture diagram |
| `docs/config.example.toml` | Configuration example |

### UNKNOWN (KEEP)

| Path | Notes |
|------|-------|
| `coworker/connectors/experimental/` | Experimental connectors — may be used in future |
