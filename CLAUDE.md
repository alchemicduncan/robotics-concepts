# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Early-stage Python project for robotics concepts, built with two complementary tools:
- **marimo** — reactive Python notebooks for interactive exploration and visualization
- **reflex** — Python-only web app framework for building the interactive frontend

Python 3.12, managed with **uv**.

## Commands

```bash
# Install dependencies
uv sync

# Run the marimo notebook editor
uv run marimo edit

# Run a specific marimo notebook
uv run marimo run <notebook.py>

# Run the Reflex web app (dev mode with hot reload)
uv run reflex run

# Run the Reflex web app for production
uv run reflex run --env prod

# Add a dependency
uv add <package>
```

## Architecture

The project uses marimo and Reflex as parallel delivery mechanisms for robotics content:

- **marimo notebooks** (`.py` files written as marimo apps) — reactive, cell-based; suited for exploratory, interactive, math-heavy content. Marimo cells are pure functions of their inputs; state flows top-to-bottom reactively.
- **Reflex app** — component-based web UI where all logic stays in Python. State is managed via `rx.State` subclasses; UI components are Python functions returning `rx.Component` trees. The Reflex compiler generates the Next.js frontend automatically.

`main.py` is currently a stub. As the project grows, expect a `rxconfig.py` (Reflex config) and an `app/` or `pages/` directory for Reflex pages alongside standalone marimo notebook files.
