# MICP HTML Authoring — Quick Reference

## File Structure

```
output-dir/
├── index.html          # Main lesson (required)
├── micp-scoring.json   # Scoring config (required for graded lessons)
└── assets/
    └── micp.js         # JS runtime (copy from skill assets)
```

Nested packaging is also valid:

```text
my-lesson/
├── index.html
├── micp-scoring.json
└── assets/
    └── micp.js
```

If you nest the lesson, keep **all referenced assets relative to that nested `index.html`**.

## Scoring Types

| Type | scoring key | response example |
|---|---|---|
| Exact match | `"correct": "B"` | `response: "B"` |
| Non-empty | `"requireNonEmpty": true` | `response: "any text"` |
| Completed | `"completed": true` | `response: "done", completed: true` |
| Presence only | `{}` (empty) | any non-null response |
| Manual review | `"gradingmode": "manual"` | `response: "free response"` |

Default rule: prefer auto-scoreable interactions for normal school activities. Use manual review only when the user explicitly wants teacher judgement.

## interactionid Rules

- Use `snake_case`: `q1_choice`, `reflection_step3`
- Prefix with context: `wave_sampling`, `binary_encode`
- Every graded interactionid must appear in BOTH `index.html` AND `micp-scoring.json`

## Default Authoring Mode

- Default to a **single-column** page that reads top to bottom.
- Put explanation, learner task, answer area, and feedback in one vertical flow.
- Use **one final submit button** in a simple submit area near the bottom.
- Do **not** show JSON logs, action traces, or debug panels in the learner UI.
- Make each core step contribute to a meaningful score.
- For text responses, prefer **constrained short answers** that can still be auto-scored after submission.
- Write instructions so a **middle school learner** can tell what to do next immediately.

## MICP SDK Calls

```js
// Initialize (once, at end of script)
window.MICP.init({ source: 'my-lesson' });

// Record an interaction
window.MICP.sendEvent('interaction', {
  interactionid: 'my_id',
  response: 'user_response_value',
  outcome: 'selected|adjusted|completed|saved|submitted',
  completed: true, // include when using "completed" scoring
  sequence: actions.length + 1,
  // ... any extra fields
});

// Submit attempt (once, when submit button clicked)
window.MICP.submit({
  raw: { actions: actions }
});
```

## Uploaded ZIP Path Rule

Moodle serves uploaded launch packages by the **full relative path** of the launch file.

- Root launch file: `index.html`
- Nested launch file: `my-lesson/index.html`

So when you author HTML:

- use `assets/micp.js`, not `/assets/micp.js`
- use relative asset URLs everywhere
- do not rely on basename-only lookup for `index.html` or other files

## Progressive Disclosure Setup

In JS setup section:
```js
var completedSteps = { 1: false, 2: false, 3: false };
var gradedInteractions = { 'q1_choice': true, 'q2_reflect': true };
var gradeStepMap = { 'q1_choice': 1, 'q2_reflect': 2 };
```

Each step's HTML has `id="step-N"` and `data-step="N"`.

Preferred step structure:

```html
<section class="step unlocked" id="step-1" data-step="1">
  <div class="step-head">...</div>
  <div class="step-body">
    <div class="viz-card">...</div>
    <div class="info-card">...</div>
  </div>
</section>
```

## Interface Guardrails

- Make one action visually primary per step.
- Use semantic tokens and the existing template classes before adding one-off styling.
- Prefer SVG icons and concept visuals; avoid emoji as core UI.
- Keep motion subtle and helpful. If you add animation, support reduced-motion.
- Cover empty, loading, saved, and error states when the lesson needs them.
- Keep the lesson browser-friendly and responsive; do not mimic a native app shell.
- Never let styling interfere with MICP hooks, interaction IDs, or submission behavior.
- Do not reveal correct/incorrect to the learner immediately by default.
- Avoid default two-column teaching layouts unless the content truly needs side-by-side comparison.
- Avoid scoreless exploration as the main activity pattern.
- After submission, show a clear human-readable result state, not internal data.

## Template Placeholders (in index.html template)

| Placeholder | Purpose |
|---|---|
| `{{TITLE}}` | Page `<title>` |
| `{{LESSON_TITLE}}` | Main heading `<h1>` |
| `{{COURSE_LABEL}}` | Hero eyebrow text |
| `{{LESSON_DESCRIPTION}}` | Short orientation paragraph |
| `{{STEPS_CONTENT}}` | Replace with step HTML |
| `{{TOTAL_STEPS}}` | Number for unlockUntil loop |
| `{{PACKAGE_SOURCE}}` | Identifier for MICP.init |
| `{{SUBMIT_BUTTON_TEXT}}` | Final submit button label |
| `{{SUBMIT_STATUS_LABEL}}` | Submit status heading |
| `{{RESULT_SCORE_LABEL}}` | Result summary score label |
| `{{INTERACTION_ID}}` | Your stable interaction ID |
