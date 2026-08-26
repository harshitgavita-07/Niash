# Niash Product Identity Audit

Generated: 2026-08-27

## Classification of Remaining OpenWorker References

### INTERNAL/TECHNICAL (KEEP)

These references are internal implementation details that would break functionality if changed.

| File | Reference | Reason to Keep |
|------|-----------|----------------|
| `pyproject.toml` | `openworker`, `openworker-server`, `openworker-connectors` CLI entry points | Would break packaging, PyInstaller spec, Tauri sidecar |
| `packaging/openworker-server.spec` | File name and `name="openworker-server"` | PyInstaller build file — changing breaks desktop builds |
| `surfaces/gui/src/api.ts` | WebSocket protocol `"openworker"` | Would break WebSocket connection between frontend and backend |
| `coworker/personas/manifest.py` | `OPENWORKER_UNSHIPPED` env var | Internal build flag for unshipped personas |
| `coworker/personas/registry.py` | `OPENWORKER_UNSHIPPED` env var | Reads the env var above |
| `coworker/server/manager.py` | `OPENWORKER_TEAM_BOARD` env var | Internal dev flag for team board |

### TEST DATA (KEEP)

These references are test fixtures and assertions that verify actual behavior.

| File | Reference | Reason to Keep |
|------|-----------|----------------|
| `surfaces/gui/e2e/fixtures.ts` | `rohit@openworker.com`, `openworker` project name | Test fixture data |
| `surfaces/gui/e2e/*.spec.ts` | Various test assertions | Test the actual behavior |
| `surfaces/gui/e2e-live/*.spec.ts` | Skip messages mentioning `openworker-server` | Instructions for test setup |
| `surfaces/gui/src/api.auth.test.ts` | `["openworker", "launch-token"]` | Tests actual WebSocket protocol |
| `surfaces/gui/src/components/GalleryModal.tsx` | `"openworker"` source key | Internal filter key, not user-facing |
| `surfaces/gui/src/components/ProjectBindMenu.test.tsx` | `openworker` project name | Test fixture data |
| `surfaces/gui/src/components/Transcript.test.tsx` | `#all-openworker` | Test fixture data |
| `tests/test_config.py` | `api.openworker.com` | Tests actual config value |
| `tests/test_connectors.py` | `rohit@openworker.com` | Test fixture data |
| `tests/test_projects.py` | `openworker` project name | Test fixture data |
| `tests/test_project_bindings.py` | `openworker` project name | Test fixture data |
| `tests/test_persona_registry.py` | `OPENWORKER_UNSHIPPED` | Tests env var behavior |
| `tests/test_devops_team.py` | `OPENWORKER_UNSHIPPED` | Tests env var behavior |
| `tests/test_devsecops_team.py` | `OPENWORKER_UNSHIPPED` | Tests env var behavior |
| `tests/test_persona_connections.py` | `OPENWORKER_UNSHIPPED` | Tests env var behavior |
| `tests/test_triage_lead.py` | `OPENWORKER_UNSHIPPED` | Tests env var behavior |
| `tests/test_server.py` | `OPENWORKER_UNSHIPPED` | Tests env var behavior |

### REBRANDED (CHANGED)

All user-facing product identity references have been changed to Niash:

- README.md — title, descriptions, download links
- Package display name (pyproject.toml)
- Desktop app name (tauri.conf.json, Info.plist, lib.rs)
- GUI brand wordmark, splash screen, onboarding
- Server HTML responses
- OAuth client name
- All user-facing strings in components
- CLI argparse prog names
- API token header
- WebSocket subprotocol
- Comments throughout codebase

### LEGAL/ATTRIBUTION (PRESERVED)

- LICENSE — MIT License, Copyright (c) 2024 Andrew Ng — preserved as required
- `docs/NIASH_BASELINE.md` — documents OpenWorker origin
- `docs/NIASH_MVP.md` — documents inherited functionality
- `pyproject.toml` — aisuite dependency reference to andrewyng/aisuite

## Summary

- **User-facing product identity**: Niash (complete)
- **Internal/technical references**: openworker (preserved for compatibility)
- **Test fixtures**: openworker (preserved to not break tests)
- **Legal/attribution**: Preserved as required

## Remaining Technical Debt

These items should NOT be touched yet:

1. CLI entry points in pyproject.toml — would break packaging
2. PyInstaller spec file name — would break desktop builds
3. WebSocket protocol identifier — would break frontend/backend connection
4. Environment variable names — would break existing deployments
5. Test fixture data — would break tests
6. package-lock.json — auto-generated, will update on next npm install
