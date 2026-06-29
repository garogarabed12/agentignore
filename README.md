# AgentIgnore

A vendor-neutral standard for excluding files and directories from AI coding agents.

**One file. One syntax. Every agent.**

## Problem

AI coding tools currently use different mechanisms, or no mechanism at all, to determine which files should be visible to agents.

This leads to:

* accidental inclusion of files that do not belong in agent context
* unnecessary token consumption
* slower indexing and retrieval
* context pollution
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

# Dependencies and generated output
node_modules/
dist/
build/
coverage/

# Tool and cache directories
.cache/
.tmp/

# Noisy runtime artifacts
*.log

# Legacy or archived code not useful for normal agent context
legacy/
archive/
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

### 🧠 Reduce Accidental Context Exposure

AgentIgnore helps prevent irrelevant files from being included in passive agent operations when they do not belong in the agent's context. This can include generated files, archives, legacy code, internal documentation, local configuration examples, or other files that are not useful for normal agent context. AgentIgnore is not a security boundary. It must not be relied on to protect secrets, private data, or confidential files from malicious tools, compromised systems, unauthorized users, or intentional exfiltration. Sensitive files still require proper access control, secret management, encryption where appropriate, and repository hygiene.


### 📦 Vendor Neutral

One ignore format that works across OpenCode, Claude Code, Aider, Roo Code, Cursor, Cline, Gemini CLI, and future agentic tools.

### 🔄 Familiar Syntax

Uses the syntax developers already know from `.gitignore`.

### 🛡️ Separate Concerns

Git controls what gets committed. AgentIgnore controls what compliant tools should exclude from passive agent operations.
These concerns overlap, but they are not the same. AgentIgnore is for context selection, retrieval quality, and interoperability; not for enforcing security policy.


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
* a security boundary
