# Contributing to AgentIgnore

Thank you for your interest in contributing to AgentIgnore.

AgentIgnore is a vendor-neutral open standard for defining which files and directories AI coding agents should exclude from passive discovery, indexing, retrieval, embedding generation, context construction, and automated modification.

This project is currently specification-first. The main contribution target is the RFC process, not a software package.

## Ways to Contribute

Useful contributions include:

* Reviewing RFC text for ambiguity or missing cases.
* Proposing changes to `.agentignore` semantics.
* Reporting compatibility issues with existing agentic coding tools.
* Suggesting examples and edge cases.
* Improving documentation.
* Opening issues about unclear behavior.
* Writing implementation notes for tools.
* Contributing compliance test cases.
* Building reference parser implementations.
* Reporting real-world adoption or experiments.

You do not need to be a maintainer to contribute.

## Before You Start

Please read:

* `README.md`
* `RFC-0001.md`
* `CODE_OF_CONDUCT.md`
* Existing GitHub issues and pull requests

Before proposing a large change, open an issue first. This avoids wasting time on a pull request that does not fit the project direction.

## Project Principles

Contributions should respect the following principles:

### Vendor neutrality

AgentIgnore should not favor one AI coding agent, company, platform, or ecosystem.

The same `.agentignore` file should be meaningful across different tools.

### Narrow scope

AgentIgnore defines file visibility behavior for AI agents.

It does not define prompts, agent instructions, workflow rules, permissions, authentication, secret storage, or full security policy.

### Compatibility with familiar ignore semantics

The project aims to use familiar `.gitignore`-style pattern behavior where possible.

Any intentional difference from `.gitignore` semantics must be clearly documented and justified.

### Passive vs. explicit access

AgentIgnore distinguishes passive agent behavior from explicit user-directed behavior.

Passive behavior includes discovery, indexing, retrieval, embedding generation, context construction, and automated modification.

Explicit behavior happens when a user directly names or requests access to a specific ignored file.

This distinction is central to the specification.

### Not a security boundary

AgentIgnore reduces accidental exposure of files to AI agents.

It must not be presented as protection against malicious tools, compromised systems, unauthorized users, or intentional data exfiltration.

Sensitive files still require proper access control, encryption, secret management, and repository hygiene.

## Opening Issues

Use issues for:

* Questions about the specification.
* Ambiguous behavior.
* Missing examples.
* Edge cases.
* Compatibility reports.
* Proposed RFC changes.
* Tool implementation feedback.
* Adoption reports.

For spec feedback, use the **[Spec Feedback](../../issues/new?template=spec-feedback.yml)** issue template. It will prompt you for the relevant area, your proposal, and your rationale.

For other issues, a good issue includes:

* A clear title.
* The relevant section of the RFC.
* The expected behavior.
* The unclear or problematic behavior.
* A concrete example if possible.

## Pull Requests

Pull requests should be focused and reviewable.

A good pull request:

* Solves one problem.
* Links to a related issue where possible.
* Explains the motivation.
* Updates examples if behavior changes.
* Avoids unrelated formatting churn.
* Preserves vendor neutrality.
* Avoids making unsupported security claims.

For specification changes, include the reasoning in the pull request description.

## RFC Process

Specification work happens through RFC documents.

RFCs should generally include:

* Title
* Status
* Authors
* Summary
* Motivation
* Goals
* Non-goals
* Specification
* Examples
* Security considerations
* Compatibility considerations
* Future work

RFC statuses are:

* `Draft`: under active discussion
* `Accepted`: approved as part of the current standard
* `Superseded`: replaced by a newer RFC or version
* `Rejected`: closed after review and not adopted

Major behavioral changes should happen through RFCs, not drive-by edits.

## Decision-Making

AgentIgnore currently uses maintainer-led rough consensus.

The maintainer will seek input from contributors, implementers, and affected tool authors before accepting major specification changes.

Consensus does not mean unanimity. A proposal may move forward if objections have been heard, discussed, and reasonably addressed.

The maintainer may reject proposals that:

* Break vendor neutrality.
* Expand the project beyond its scope.
* Create unclear or untestable behavior.
* Conflict with core RFC principles.
* Add complexity without enough benefit.
* Make misleading security guarantees.

As the project grows, governance should move toward a multi-maintainer model with representation from different organizations and tool ecosystems.

## Style Guidelines

Use clear, direct technical language.

Prefer:

```text
Compliant tools MUST exclude ignored files from passive context construction.
```

Avoid:

```text
Tools should probably try not to look at ignored files in normal situations.
```

Use RFC-style terms carefully:

* `MUST` means required.
* `MUST NOT` means forbidden.
* `SHOULD` means strongly recommended unless there is a good reason.
* `MAY` means optional.

Do not use these terms casually.

## Examples and Test Cases

Examples are extremely valuable.

When adding examples, include:

* The `.agentignore` file.
* A small example file tree.
* The expected visible and ignored files.
* Whether the scenario concerns passive access or explicit user-directed access.

Example:

```text
.agentignore:
.env
secrets/

File tree:
.env
src/app.ts
secrets/api-key.txt
README.md

Passive agent context SHOULD include:
src/app.ts
README.md

Passive agent context MUST NOT include:
.env
secrets/api-key.txt
```

## Tool Compatibility Reports

If you test AgentIgnore behavior against an AI coding tool, please report:

* Tool name
* Tool version
* Operating system
* Repository structure
* `.agentignore` contents
* Observed behavior
* Expected behavior
* Any relevant logs or screenshots

Do not include secrets, private files, or confidential repository contents.

## License of Contributions

Unless otherwise stated, contributions to this repository are submitted under the repository license.

By contributing, you confirm that you have the right to submit your contribution and that it can be included in the project.

## Code of Conduct

All contributors must follow `CODE_OF_CONDUCT.md`.

Technical criticism is welcome. Personal attacks are not.
