# AgentIgnore

A vendor-neutral standard for excluding files and directories from AI coding agents.

**One file. One syntax. Every agent.**

## Problem

AI coding tools currently use different mechanisms, or no mechanism at all, to determine which files should be visible to agents.

This leads to:

* unnecessary token consumption
* slower indexing and retrieval
* context pollution
* accidental exposure of sensitive information
* inconsistent behavior across tools

## Prior Art

AgentIgnore is an emerging community effort to standardize file exclusion for AI coding agents.

The `.agentignore` concept has emerged (independently) across multiple projects and communities:

* Repository: [agentignore](https://github.com/tourcoder/agentignore/) ([tourcoder](https://github.com/tourcoder))
* Repository: [claude-agentignore, a Claude Code hook implementation](https://github.com/yurekami/claude-agentignore) ([yurekami](https://github.com/yurekami))
* Issue: [Specification extension request: standardized ignore files support in Agents.md specification](https://github.com/agentsmd/agents.md/issues/33) ([agentsmd/agents.md](https://github.com/agentsmd/agents.md))
* Issue: [Feature request: .claudeignore - exclude files from Claude Code's context](https://github.com/anthropics/claude-code/issues/29455) ([anthropics/claude-code](https://github.com/anthropics/claude-code))
* Issue: [Introduce and use a standard for AI agent ignore file](https://github.com/google-gemini/gemini-cli/issues/4688) ([google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli))
* Issue: [A way to exclude sensitive files](https://github.com/openai/codex/issues/2847) ([openai/codex](https://github.com/openai/codex))
* Issue: [Feature request: .codexignore/.aiignore file](https://github.com/openai/codex/issues/24993) ([openai/codex](https://github.com/openai/codex))
* Issue: [Feature request: .claude-ignore support](https://github.com/anthropics/claude-code/issues/30810) ([anthropics/claude-code](https://github.com/anthropics/claude-code))
* Discussion: [Standardize on .agentignore format support](https://github.com/orgs/agentclientprotocol/discussions/49) ([agentclientprotocol](https://github.com/agentclientprotocol))
* Discussion: [Feature request: support for .agentignore in Cline](https://github.com/cline/cline/discussions/5887) ([cline/cline](https://github.com/cline/cline))

This project does not claim invention of the idea. Its goal is to provide a formal RFC and compatibility requirements that can help the ecosystem converge on a single vendor-neutral standard.

## Solution

AgentIgnore introduces a dedicated `.agentignore` file that allows developers to explicitly control which files and directories should be visible to AI coding agents.

## Example

```text
# .agentignore

node_modules/
dist/
*.log
*.env
legacy/
```

## Specification

* [RFC-0001](RFC-0001.md)

## Why AgentIgnore?

### 💰 Reduce Token Costs

AI agents shouldn't waste tokens analyzing files that are irrelevant to the task.

### ⚡ Faster Context Building

Smaller search spaces mean faster indexing, retrieval, and reasoning.

### 🎯 Improve Retrieval Quality

Exclude noise such as archives, generated artifacts, and legacy code to help agents focus on what matters.

### 🔒 Protect Sensitive Information

Prevent agents from automatically discovering or processing files containing credentials, customer data, compliance documents, or other sensitive content.

### 🧠 Reduce Context Pollution

Irrelevant files can distract agents and degrade the quality of their responses.

### 📦 Vendor Neutral

One ignore format that works across OpenCode, Claude Code, Aider, Roo Code, Cursor, Cline, Gemini CLI, and future agentic tools.

### 🔄 Familiar Syntax

Uses the syntax developers already know from `.gitignore` .

### 🛡️ Separate Security Concerns

Git protects against accidentally committing files.

AgentIgnore protects against accidentally exposing files to AI agents.

### 🤖 Agent Visibility ≠ Git Visibility

Version control and AI context management solve different problems and therefore deserve different standards.

### 📚 Keep Documentation in Git

Some files should remain version-controlled but should not be used as agent context.

## Status

> AgentIgnore is currently in the proposal phase.

The specification is not yet finalized and may change based on community feedback.

## What AgentIgnore is NOT

AgentIgnore is not:

* an agent instruction format
* a prompt engineering framework
* a workflow orchestration system
* a replacement for AGENTS.md
* a replacement for CLAUDE.md
* a replacement for Git
