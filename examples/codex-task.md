# Agent Task Pollution Example

## Scenario

A user wants a clean task for a downstream coding agent. The upstream model must remove negotiation, self-protection, and connector-specific caution that does not belong in the agent task.

## Bad example

```text
Do not assume the GitHub username, do not write a fixed owner, and use the currently connected GitHub account to create the repository.
```

## Problem

This is the model's self-protective instruction, not an engineering task for the downstream agent. It leaks upstream correction traces and turns the downstream task into a record of the user-model negotiation.

## Good example

```text
Create the repository canproom-audio and implement a minimal verifiable Web Audio test bench.

Requirements:
- Add a browser-based page that can start and stop a generated tone.
- Display the active audio state.
- Include setup and verification steps in the README.
- Use an MIT license.

Acceptance criteria:
- The page runs locally in a browser.
- The tone start and stop controls work.
- The README explains how to verify the behavior.
```
