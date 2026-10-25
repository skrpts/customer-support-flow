# Release Notes

## v1.1.32
GH#1100 consumer wave (batch 3) — declare the data flow this workflow was resolving positionally.

Each stage below now receives its input through a declared `bindings:` entry instead of `default_from_previous`, which K-073 revoked. **The value is unchanged**: every binding names the step that immediately precedes it, which is exactly what the positional default resolved to. What changes is that the dependency is stated rather than inferred from position, so a reorder can no longer silently feed a stage the wrong artefact.

Bindings added:
  `adapt-tone` ← `from_step: "Response Drafting"` (step 3)
  `polish-language` ← `from_step: "Tone Adaptation"` (step 4)
  `extract-structured-data` ← `from_step: "Language Polish"` (step 5)

Dependency pins moved to the published versions that declare these slots:
  `adapt-tone` 1.0.3 → 1.0.4
  `draft-response` 1.0.3 → 1.0.4
  `extract-structured-data` 1.0.1 → 1.0.3
  `format-conversion` 1.0.4 → 1.0.5
  `intent-classification` 1.0.1 → 1.0.2
  `polish-language` 1.0.1 → 1.0.7
  `structured-data-extraction` 1.0.1 → 1.0.2

## v1.1.31
GH#1100 wave B — run the PII masking step instead of silently not running it.

The step named `skill: pii-masking` with `step_type: local.transform`, which is not a step type the engine can execute, and the shared bundle shipped no prompt to run — so the masking stage reached no handler. `_shared/pii-masking@1.0.4` now ships the prompt (GH#1100 bucket 1), so the step becomes a real content step: `prompt: pii-masking`, and the content to mask is wired explicitly with `bindings: source` from `Format Conversion` rather than read positionally. Dependency pin 1.0.1 → 1.0.4, checksum resolved against live Hub rather than transcribed.

## v1.1.30
GH#1070 — the format-conversion step could not run. It now runs, and converts the extracted conversation data into a readable form.

The step was declared with a step type the engine does not dispatch, so it failed instead of converting. It now runs the shared format-conversion skill the same way the code-review, documentation and sprint-wrapup pipelines already run it, with the target format declared on the step (`markdown`) rather than left for the skill to guess — the skill supports six formats, and this step needs the one that stays readable for both storage and hand-off.

**This skrpt is hidden from browse and search.** Its PII-masking step cannot run yet — it fails rather than processing anything unmasked, so nothing is mishandled, but the pipeline cannot complete. That needs a deterministic masking step the engine does not have yet (GH#1064). It is now the only step still failing. If you have it installed, keep it: the fix will reach you as a normal update when that lands.

## v1.1.29
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.28
GH#745 — declare per-step `output: {name, type}` on every execution step (intent/text, draft_response/text, toned_response/text, polished_response/text, structured_data/json, formatted_response/text, masked_response/text). Lights up the #744 rich flow-map. Content-only; no bindings or logic changes.

## v1.1.27
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 14 inline shared-content files and declare 14 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.26
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.25
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.24
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.23
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.22
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
