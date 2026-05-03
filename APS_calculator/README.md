# Phase 1 Re-Annotation Platform

This folder now contains a dependency-free annotation web app for the Phase 1 human review workflow.

The folder name remains `APS_calculator` for continuity, but the app itself is no longer a score or tier calculator.

## What it does

- loads `annotation_template.csv` or an existing `annotator_*.csv`
- connects the local `agentdojo/runs` folder to show the full original trace on demand
- renders injections, messages, tool calls, tool outputs, and raw JSON in a reviewer-friendly timeline
- presents the `human_*` fields as a survey-style annotation form with inline explanations
- starts the survey with `framework_applicable` and `adversarial_objectives`, so annotators decide attacker intent before propagation depth and can mark benign traces with `["none"]`
- saves browser-session progress locally
- exports a standard annotation CSV
- exports an enriched CSV that also appends:
  - `original_trace_excerpt`
  - `original_trace_json`

## Expected workflow

1. Open `index.html`.
2. Load `\annotation_template.csv`.
3. Connect the local `\runs` folder.
4. Decide whether the framework applies, then choose either `none` for a benign/non-applicable trace or the relevant `O1` / `O2` / `O3` objectives.
5. Complete and save each annotation entry.
6. Export your CSV as `annotator_A.csv` or `annotator_B.csv`.

## Files

- `index.html`: app shell and survey layout
- `styles.css`: responsive visual system for trace review and form entry
- `app.js`: CSV parsing, trace loading, annotation state, validation, and export logic

## Open locally

You can open `index.html` directly in a browser, or serve the folder with a small static server.

Example:

```bash
python -m http.server
```
