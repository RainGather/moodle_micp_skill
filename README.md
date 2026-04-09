# MICP Authoring Skill

[**中文版**](./README_zh.md)

> **The old way:** a teacher has an interactive teaching idea, then gets stuck turning it into HTML, packaging, event tracking, and grading rules.
> **The MICP way:** the agent generates a full lesson package that is ready to upload into MICP.

`MICP Authoring Skill` is a general AI-agent skill and authoring pack for generating complete lesson packages for the `mod_micp` Moodle activity module.

The workflow is not tied to a single tool vendor. It can be adapted for Codex, OpenCode, OpenClaw, Claude Code, and similar agentic tools that can follow repository instructions and generate files from structured references. `SKILL.md` is the packaged form in this repository, but the authoring method itself is tool-agnostic.

The skill focuses on one job: produce a deployable MICP lesson package with the files Moodle needs:

```text
output-dir/
├── index.html
├── micp-scoring.json
└── assets/
    └── micp.js
```

## Why Teachers And Course Teams Care

Teachers often know the activity they want students to do. The real problem is converting that idea into something usable inside a course without becoming a front-end developer and assessment engineer.

This skill is meant to reduce that gap. It helps an AI agent generate lesson packages that are not just visually interactive, but operational for teaching:

- structured enough to upload into `mod_micp`
- instrumented enough to capture learner evidence
- constrained enough to support reliable server-side scoring
- flexible enough to support simulations, explorations, guided tasks, and reflective prompts

The practical outcome is that a teacher or course team can move from "activity idea" to "uploadable lesson package" much faster, with less hand-built HTML and much less ambiguity around grading.

## The Core Loop

```text
Teaching idea -> agent generates MICP package -> upload to MICP -> students use it in Moodle
```

That is the promise of this repository: not generic HTML generation, but lesson-package generation that fits a real teaching workflow.

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

- `SKILL.md` is the canonical runtime instruction file in this repository
- the same authoring workflow can be reused in other agent environments, even if they package instructions differently
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

Use this repository when you need an AI agent to create a MICP-compatible lesson package for Moodle.

Depending on your environment, that may mean:

- installing it as a skill in Codex-compatible tooling
- adapting `SKILL.md` into another agent's instruction format
- reusing the references and templates as a portable authoring pack

Typical triggers include:

- create an interactive HTML lesson for mod_micp
- generate a MICP package
- create a progressive disclosure lesson for Moodle
- 制作 MICP 互动课件

## Relationship To mod_micp

This repository contains authoring guidance and bundled references for generating lesson packages.
It is separate from the Moodle plugin repository itself, which is responsible for delivering, storing, and grading those packages inside Moodle.

## Teaching Use Cases

This skill is especially useful when teachers want to produce:

- guided multi-step activities
- interactive explanations with embedded checks
- visual explorations followed by evidence capture
- mixed auto-graded and manually reviewed tasks
- reusable activity packages for a department or course team

The main gain is not novelty for its own sake. The gain is reducing the cost of producing stronger interactive activities that still fit a real Moodle teaching workflow.

## License

GPL v3 or later. See [LICENSE](./LICENSE).
