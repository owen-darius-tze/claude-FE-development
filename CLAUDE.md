# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This repository is a **fresh-start reset** for a Flyrank AI internship project. It currently contains only `README.md`, `LICENSE` (MIT), and `.gitignore` — no source code, build configuration, or tooling has been added yet. Treat the project as greenfield: there is no package manager, test runner, or lint config to invoke until one is introduced.

Per the README, this is the second attempt at a frontend (FE) development repository; the first was abandoned because its output "completely deviates from what I want." **Before generating substantial code, confirm the desired framework, structure, and feature scope with the user** to avoid repeating that divergence.

## Environment notes

- The committed `.gitignore` is GitHub's standard **Python** template (ignores `__pycache__`, `.venv`, `.pytest_cache`, etc.). Despite the "FE development" framing, no Node/JS/web tooling ignores (e.g. `node_modules`, `dist`, `.next`) are present. If the project turns out to be JS/TS-based, update `.gitignore` accordingly; the current template does not cover typical frontend artifacts.
- Repository is on the `main` branch with a single `Initial commit`; remote is `https://github.com/owen-darius-tze/claude-FE-development.git`. Strictly read-only remote operations are fine; do not push without explicit instruction.
- Working directory on disk is nested one level inside the parent folder (`.../claude-FE-development/claude-FE-development/`) — the repo root is the inner directory.
