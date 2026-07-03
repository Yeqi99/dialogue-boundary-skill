# Agent Task Pollution Example

## Scenario

A user wants a clean task for a downstream coding agent. The upstream model must remove negotiation, self-protection, and connector-specific caution that does not belong in the agent task.

## Bad example

```text
Do not assume the GitHub username, do not write a fake owner, and use the currently connected GitHub account to create the repository. I am saying this because I need to avoid leaking an incorrect assumption to the user.
```

## Problem

This is the model's self-protective explanation, not an engineering task for the downstream agent. It leaks upstream reasoning and turns the agent task into a trace of the user-model negotiation.

## Good example

```text
Create the repository canproom-audio and implement a minimal verifiable Web Audio test bench.

Requirements:
- Create a public repository named canproom-audio.
- Add a small browser-based Web Audio page that can generate a tone, stop playback, and display the active oscillator state.
- Include a README with setup and verification steps.
- Add an MIT license.

Acceptance criteria:
- The page runs locally in a browser.
- The tone start and stop controls work.
- The README explains how to verify the behavior.
```
