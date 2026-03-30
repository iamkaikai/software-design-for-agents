# Software Design for Agents — Repo Guidelines

This repo contains software design rules from *A Philosophy of Software Design*, structured for AI coding agents.

## Structure

- `rules/` — One file per design principle. Each has frontmatter (name, chapter, tags) and sections (Principle, Why It Matters, How to Apply, Red Flags, Examples).
- `rules/_index.md` — Master index of all rules with chapter numbers, tags, and file links. Start here to find a rule by topic.
- `rules/_coverage.md` — Maps every chapter (1–21) of *A Philosophy of Software Design* to its rule file. Use this to check which chapters are covered and how.
- `profiles/` — Task-specific rule sets (plan, implement, review, refactor, debug). Each profile references rules in priority order.

## Conventions

- Rule files use YAML frontmatter with `name`, `chapter`, and `tags` fields.
- Profile files reference rules using relative links to the rules directory.
- Keep `rules/_index.md` in sync when adding/removing/renaming rules.
