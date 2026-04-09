# MICP Lesson Package Builder

[**中文版**](./README_zh.md)

This repository is not the Moodle plugin itself.

It is a reusable AI authoring guide for making lesson packages that can be uploaded into MICP for Moodle.

In plain language:

- the Moodle plugin runs the activity in class
- this repository helps an AI assistant create the lesson package for that activity

## Who This Is For

This repository is for teachers, course teams, or developers who want help generating interactive lesson packages.

It is useful when you want an AI assistant to help you create:

- a guided lesson page
- a multi-step learning activity
- a visual interactive explanation
- a practice activity with automatic scoring
- a mixed activity with both auto-scored and teacher-reviewed parts

## What It Produces

The target output is a lesson package like this:

```text
output-dir/
├── index.html
├── micp-scoring.json
└── assets/
    └── micp.js
```

That package can then be uploaded into the MICP Moodle plugin.

## How A Teacher Can Understand It

If you do not care about AI tooling details, the simplest way to think about this repository is:

1. Give these instructions to an AI assistant.
2. Ask it to create a lesson on your teaching topic.
3. The assistant generates a MICP lesson package.
4. Upload that package into Moodle through the MICP plugin.

So this repository is a "lesson package builder guide" for AI assistants.

## Is It Only For Codex

No.

The workflow is not tied to one vendor or one coding assistant. It can be adapted for:

- Codex
- OpenCode
- OpenClaw
- Claude Code
- similar agent tools that can follow repository instructions and generate files

`SKILL.md` is the packaged instruction format used in this repository, but the method itself is general.

## Why It Matters In Teaching

Many teachers can describe a strong interactive activity, but building it from scratch is slow.

Usually the work gets stuck in one of these places:

- writing the HTML
- deciding how to capture student actions
- deciding how to score the activity
- packaging everything in a form Moodle can actually use

This repository is meant to reduce that burden.

Its goal is not "make fancy pages". Its goal is "help produce uploadable teaching activities that really work inside Moodle".

## Basic Usage

### Option 1. Use it with an AI assistant

Give the repository or the `SKILL.md` instructions to your AI assistant and ask for a lesson package, for example:

```text
Create a MICP lesson about photosynthesis for secondary school students.
```

The assistant should generate:

- `index.html`
- `micp-scoring.json`
- any needed assets

### Option 2. Reuse the templates manually

If needed, developers can also reuse the templates, patterns, and assets directly.

## Repository Layout

```text
.
├── SKILL.md
└── references/
    ├── assets/
    ├── patterns/
    ├── templates/
    └── quick-reference.md
```

- `SKILL.md` is the main instruction file
- `references/` contains templates, interaction patterns, and assets
- this README is repository-level documentation for humans

## Relationship To The Moodle Plugin

This repository creates lesson packages.

The Moodle plugin repository runs those packages inside Moodle, records learner activity, scores it, and reports it.

The two repositories are related, but they do different jobs.

## License

GPL v3 or later. See [LICENSE](./LICENSE).
