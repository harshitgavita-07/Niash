# Niash Dependency Audit

Generated: 2026-08-27

## Python Dependencies (pyproject.toml)

### Core Dependencies

| Package | Version | Purpose | Status |
|---------|---------|---------|--------|
| `openai` | >=1.0 | OpenAI API provider | REQUIRED |
| `anthropic` | >=0.40 | Anthropic Claude API provider | REQUIRED |
| `google-genai` | >=1.0 | Google Gemini API provider | REQUIRED |
| `google-auth` | >=2.23 | Vertex AI credentials | REQUIRED |
| `textual` | >=1.0 | Terminal UI framework | REQUIRED |
| `fastapi` | >=0.110 | HTTP server framework | REQUIRED |
| `uvicorn[standard]` | >=0.27 | ASGI server | REQUIRED |
| `aisuite` | git+andrewyng/aisuite | Unified LLM API + agents | REQUIRED |
| `docstring_parser` | any | Docstring parsing | REQUIRED |
| `pyyaml` | >=6 | YAML parsing (personas) | REQUIRED |
| `pydantic` | >=2 | Data validation | REQUIRED |
| `mcp` | >=1.28.1,<2 | MCP client protocol | REQUIRED |
| `httpx` | >=0.27 | HTTP client | REQUIRED |
| `websockets` | >=13 | WebSocket client (Slack) | REQUIRED |
| `ddgs` | >=9 | DuckDuckGo search | REQUIRED |
| `croniter` | >=2 | Cron scheduling | REQUIRED |
| `pypdf` | >=5 | PDF text extraction | REQUIRED |
| `pypdfium2` | >=4 | PDF rasterization | REQUIRED |
| `tzdata` | sys_platform=='win32' | Windows timezone data | CONDITIONAL |
| `tomli` | python_version<'3.11' | TOML parsing (Python<3.11) | CONDITIONAL |

### Optional Dependencies

| Group | Packages | Purpose | Status |
|-------|----------|---------|--------|
| `dev` | pytest>=8, pytest-asyncio, httpx | Testing | OPTIONAL |
| `messaging` | python-telegram-bot>=21, slack-bolt>=1.18, aiohttp>=3.9 | Inbound messaging | OPTIONAL |
| `browser` | playwright>=1.44 | Browser automation | OPTIONAL |
| `bedrock` | boto3>=1.34 | AWS Bedrock provider | OPTIONAL |

## npm Dependencies (surfaces/gui/package.json)

### Runtime Dependencies

| Package | Version | Purpose | Status |
|---------|---------|---------|--------|
| `pdfjs-dist` | ^4.10.38 | PDF rendering | REQUIRED |
| `react` | ^18.3.1 | UI framework | REQUIRED |
| `react-dom` | ^18.3.1 | React DOM | REQUIRED |
| `react-markdown` | ^10.1.0 | Markdown rendering | REQUIRED |
| `remark-gfm` | ^4.0.1 | GitHub Flavored Markdown | REQUIRED |
| `simple-icons` | ^16.26.0 | Brand icons | OPTIONAL |
| `xlsx` | ^0.18.5 | Excel file support | OPTIONAL |

### Dev Dependencies

| Package | Version | Purpose | Status |
|---------|---------|---------|--------|
| `@playwright/test` | ^1.61.1 | E2E testing | OPTIONAL |
| `@tauri-apps/cli` | ^2.11.2 | Tauri CLI | OPTIONAL |
| `@testing-library/dom` | ^10.4.1 | DOM testing | OPTIONAL |
| `@testing-library/react` | ^16.3.2 | React testing | OPTIONAL |
| `@types/react` | ^18.3.3 | TypeScript types | OPTIONAL |
| `@types/react-dom` | ^18.3.0 | TypeScript types | OPTIONAL |
| `@vitejs/plugin-react` | ^4.3.1 | Vite React plugin | OPTIONAL |
| `autoprefixer` | ^10.5.2 | CSS autoprefixer | OPTIONAL |
| `jsdom` | ^25.0.1 | DOM simulation | OPTIONAL |
| `postcss` | ^8.5.16 | CSS processing | OPTIONAL |
| `tailwindcss` | ^3.4.19 | CSS framework | OPTIONAL |
| `typescript` | ^5.5.3 | TypeScript compiler | OPTIONAL |
| `vite` | ^5.4.0 | Build tool | OPTIONAL |
| `vitest` | ^2.1.9 | Unit testing | OPTIONAL |

## Rust Dependencies

### Tauri Shell (surfaces/gui/src-tauri/Cargo.toml)

| Package | Version | Purpose | Status |
|---------|---------|---------|--------|
| `tauri` | 2 | Desktop shell framework | REQUIRED |
| `tauri-plugin-dialog` | 2 | File dialogs | REQUIRED |
| `tauri-plugin-autostart` | 2 | Auto-start | REQUIRED |
| `tauri-plugin-single-instance` | 2 | Single instance | REQUIRED |
| `tauri-plugin-updater` | 2 | Auto-update | REQUIRED |
| `serde` | 1 | Serialization | REQUIRED |
| `serde_json` | 1 | JSON serialization | REQUIRED |
| `uuid` | 1 | UUID generation | REQUIRED |
| `ocw-stt` | local | Speech-to-text | REQUIRED |

### Speech-to-Text (stt/Cargo.toml)

| Package | Version | Purpose | Status |
|---------|---------|---------|--------|
| `cpal` | 0.15.3 | Audio input | REQUIRED |
| `serde` | 1 | Serialization | REQUIRED |
| `sha2` | 0.10 | Hashing | REQUIRED |
| `ureq` | 2.12 | HTTP client | REQUIRED |
| `whisper-rs` | 0.16 | Whisper model | REQUIRED |

## Audit Findings

### All Dependencies Used

All declared dependencies are actively used by the codebase:

- **Python**: Core runtime, providers, connectors, server, MCP, memory, automation
- **npm**: GUI framework, PDF rendering, markdown, build tooling
- **Rust**: Desktop shell, speech-to-text

### No Unused Dependencies Identified

Each dependency has clear usage:
- `textual` — TUI implementation in `coworker/tui/`
- `pypdf`/`pypdfium2` — PDF support in `coworker/pdf_support.py`
- `ddgs` — Web search in connectors
- `croniter` — Automation scheduling
- `websockets` — Slack relay client
- `simple-icons` — Brand icons in GUI
- `xlsx` — Excel file support in GUI

### Recommendations

1. **aisuite** — Currently pinned to a git commit. Consider upgrading to PyPI release when available.
2. **Package-lock.json** — Will auto-update on next `npm install`. No manual action needed.
3. **No dependency removals recommended** — All are actively used.

## Status

- **Python**: 18 core + 4 optional groups
- **npm**: 7 runtime + 14 dev
- **Rust**: 9 (Tauri) + 5 (STT)
- **Total**: 53 dependencies across all platforms
