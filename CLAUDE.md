# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a multi-agent content-creation system. A primary "CEO" orchestrator agent coordinates a team of specialized sub-agents, each responsible for a different aspect of content production. The agent roster and their responsibilities will be defined incrementally.

## Project-Specific Claude Configuration

The `.claude/` directory contains customizations for this project:

- `.claude/agents/` — sub-agent definitions (personas, system prompts, tool access)
- `.claude/skills/` — reusable skill files invokable via slash commands
- `.claude/commands/` — custom slash commands for project workflows
