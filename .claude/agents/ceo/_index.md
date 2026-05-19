# .claude/agents/ceo — Index

CEO Agent — the root orchestrator contract. Loaded by `CLAUDE.md` on every session start.

This folder uses **folder form** (`ceo/agent.md`) so Claude Code does **not** auto-discover it as a Task-invokable sub-agent. The CEO is the main session, not a sub-agent.

Single-file sub-agents (auto-discovered, invokable via the Task tool) belong directly at `.claude/agents/<name>.md` with YAML frontmatter.

## Files

- [[agent]] — CEO Agent behavioral contract (identity, sub-agent registry, routing rules, execution protocol, language rules, constraints, output format, error handling)
