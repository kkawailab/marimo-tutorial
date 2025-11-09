# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a tutorial repository for marimo, a reactive Python notebook environment. The primary content is a comprehensive Japanese-language tutorial (`marimo_tutorial_ja.md`) covering installation, basic concepts, and usage examples.

## Repository Structure

- `marimo_tutorial_ja.md` - Main Japanese tutorial document covering marimo from installation through advanced usage
- `.claude/` - Claude Code configuration

## Working with This Repository

### Testing Tutorial Examples

When users want to test examples from the tutorial:

1. Create a Python virtual environment:
   ```bash
   python -m venv marimo-env
   source marimo-env/bin/activate  # macOS/Linux
   # marimo-env\Scripts\activate  # Windows
   ```

2. Install marimo:
   ```bash
   pip install marimo
   # or for full features:
   pip install "marimo[recommended]"
   ```

3. Run tutorial notebooks:
   ```bash
   marimo tutorial intro
   marimo edit example.py  # to create/edit notebooks
   ```

### Creating Example Notebooks

When creating example marimo notebooks based on tutorial content:
- Save as `.py` files (marimo notebooks are pure Python)
- Each cell should define variables uniquely (no variable redefinition across cells)
- Use `import marimo as mo` convention
- Remember marimo's reactive execution model - cells auto-execute based on variable dependencies

### Language

The tutorial is written in Japanese. When updating or extending the tutorial, maintain Japanese language and formatting consistency.
