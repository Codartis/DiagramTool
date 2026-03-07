# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is the **product support and documentation repository** for Codartis Diagram Tool, a Visual Studio extension for interactive C# code visualization. It contains no source code — only Markdown documentation, images, and support resources.

## Structure

- `README.md` — Product support landing page with links to help topics and support channels
- `help/v2/` — Current documentation (v2.x): getting-started, how-to-use, diagram-notation, troubleshooting
- `help/v2/images/` — Screenshots for v2 docs
- `help/Help.md` — Legacy v1.x documentation
- `help/images/` — Screenshots for v1 docs
- `images/` — Product logo files

## Documentation Conventions

- Help content is versioned: v2 docs live under `help/v2/`, v1 docs remain at `help/Help.md`
- Each help page uses a table of contents at the top with anchor links
- Screenshots are PNG files stored in the corresponding `images/` subdirectory
- Commit messages follow the pattern: "Updated help for vX.Y.Z" for release-aligned updates

## No Build/Test System

There are no build, lint, or test commands. All content is static Markdown and images.
