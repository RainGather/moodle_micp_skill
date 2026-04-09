# micp-html-authoring

`micp-html-authoring` is a Codex skill for generating complete lesson packages for the `mod_micp` Moodle activity module.

The skill focuses on one job: produce a deployable MICP lesson package with the files Moodle needs:

```text
output-dir/
├── index.html
├── micp-scoring.json
└── assets/
    └── micp.js
```

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

- `SKILL.md` is the canonical runtime instruction file consumed by Codex.
- `references/` contains templates, interaction patterns, and bundled runtime assets used when authoring lesson packages.
- This README is repository-level documentation for version control and publication. It is not part of the skill loading contract.

## What The Skill Covers

- MICP-compatible HTML lesson authoring
- Progressive step interactions
- Proper `window.MICP` SDK usage
- Server-side scoring config generation
- Packaging conventions for Moodle `mod_micp`
- Guardrails for UI clarity, accessibility, and grading integrity

## Usage

Install or copy this skill into a Codex skills directory, then invoke it when you need to create a MICP-compatible lesson package for Moodle.

Typical triggers include:

- create an interactive HTML lesson for mod_micp
- generate a MICP package
- create a progressive disclosure lesson for Moodle
- 制作 MICP 互动课件

## Relationship To mod_micp

This repository contains authoring guidance and bundled references for generating lesson packages.
It is separate from the Moodle plugin repository itself, which is responsible for delivering, storing, and grading those packages inside Moodle.

## License

GPL v3 or later. See [LICENSE](./LICENSE).
