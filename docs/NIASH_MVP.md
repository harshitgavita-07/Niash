# Niash MVP

## Product Thesis

> Humans and AI should be able to work on the same computer at the same time.

## MVP Scope

### 1. Existing Agent/Task Runtime
- Inherited from OpenWorker codebase
- Multi-turn conversation with tool calling
- Context management and compaction
- Auto-approve reviewer for safety

### 2. Small Human ↔ AI Interaction Surface
- Desktop GUI for concurrent interaction
- Real-time transcript with streaming
- Approval cards for gated actions
- Ask-user for clarifying questions

### 3. Human Activity Awareness
- Detect when human is actively using the computer
- Track mouse/keyboard activity
- Adapt agent behavior based on human presence

### 4. Computer/Application Context
- Access to filesystem and terminal
- Browser automation capabilities
- Application state awareness
- System resource monitoring

### 5. Background AI Tasks
- Scheduled automations (cron-based)
- Unattended mode with inbox routing
- Durable resume for interrupted sessions

### 6. Shared Computer-Resource Arbitration
- Prevent conflicts between human and agent actions
- Coordinate terminal usage
- Manage concurrent file access
- Resource priority system

### 7. Human Priority When Physical Interaction Conflicts
- Detect physical input (mouse/keyboard) during agent operations
- Yield to human input automatically
- Pause or defer agent actions when human is active

### 8. Local/Cloud Model Neutrality
- Support multiple LLM providers
- Local model support (Ollama)
- Cloud API support (OpenAI, Anthropic, Google, etc.)
- Easy provider switching

### 9. Safe Interruption
- Graceful agent pause on human input
- State preservation during interruption
- Resume from interruption point
- No data loss on interruption

### 10. Verification
- Test suite for core functionality
- Integration tests for connectors
- E2E tests for GUI
- Security review gate

## Design Principles

1. **Local-first** — Everything runs on the user's machine
2. **Human-in-the-loop** — Agent checks before consequential actions
3. **Non-blocking** — Human can always take control
4. **Transparent** — Full transcript and audit trail
5. **Composable** — MCP protocol for extensibility

## NOT in MVP

- Shared cursor/pointer
- Interaction lease system
- Reaction engine
- Agent swarm coordination
- Persistent background loops
- New memory architecture
- Voice interaction
- VM/container support
- macOS-specific features
- New model providers

## Next Steps (Post-MVP)

1. Shared cursor implementation
2. Interaction lease protocol
3. Reaction engine for real-time feedback
4. Agent swarm coordination
5. Persistent background loops
6. Enhanced memory system
7. Voice interaction
8. VM/container support
