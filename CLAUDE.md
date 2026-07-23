# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This repository is a **fresh-start reset** for a Flyrank AI internship project. It currently contains only `README.md`, `LICENSE` (MIT), and `.gitignore` — no source code, build configuration, or tooling has been added yet. Treat the project as greenfield: there is no package manager, test runner, or lint config to invoke until one is introduced.

Per the README, this is the second attempt at a frontend (FE) development repository; the first was abandoned because its output "completely deviates from what I want." **Before generating substantial code, confirm the desired framework, structure, and feature scope with the user** to avoid repeating that divergence.

## Environment notes

- The committed `.gitignore` is GitHub's standard **Python** template (ignores `__pycache__`, `.venv`, `.pytest_cache`, etc.). Despite the "FE development" framing, no Node/JS/web tooling ignores (e.g. `node_modules`, `dist`, `.next`) are present. If the project turns out to be JS/TS-based, update `.gitignore` accordingly; the current template does not cover typical frontend artifacts.
- Repository is on the `main` branch with a single `Initial commit`; remote is `https://github.com/owen-darius-tze/claude-FE-development.git`. Strictly read-only remote operations are fine; do not push without explicit instruction.
- Working directory on disk is nested one level inside the parent folder (`.../claude-FE-development/claude-FE-development/`) — the repo root is the inner directory.

## Learned project rules (from generating the inquiry forms from scratch)

These rules were established while generating the `vague-inquiry-form` and `precise-inquiry-form` work. Follow them for all future form / frontend work in this repo.

1. **Ask before generating substantial code.** The first attempt at this repo was abandoned because its output "completely deviates from what I want." This repo's standing instruction is to confirm framework, structure, and feature scope with the user *before* writing substantial code. Ask clarifying questions (form purpose, tech approach, submit handling) even when the task seems clear — divergence is the known failure mode here, not over-asking.

2. **One self-contained file unless told otherwise.** When the user says "basic" or wants no build tooling, put HTML/CSS/JS in a single `index.html` rather than splitting into linked files. Both inquiry forms `vague` and `precise` follow this. Split files only if the user asks for separation or a build step.

3. **Confirm scope vs. promise before declaring a feature "working."** Forms in this repo are client-side only with no backend. A "working" submit button still means a banner/validation, not actual data persistence. State this honestly in the message to the user and in doc files (see `WORKFLOW.md`) — never imply data is sent somewhere it isn't. Empty `action=""` is a placeholder, not a feature.

4. **Branches, not big-bang commits to `main`.** The two inquiry forms live on separate feature branches (`vague-inquiry-form`, `precise-inquiry-form`) off `main`. Prefer a feature branch per distinct attempt/variant so they can be diffed and reviewed independently. Do not push without explicit instruction (per the environment notes above) — local branches are fine.
