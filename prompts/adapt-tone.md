---
type: prompt
id: adapt-tone
title: "Adapt Tone"
description: "Rewrites text to match a specified tone whilst preserving meaning"
tags: [Production, Writing]
connections:
  - target: tone-adaptation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Drives the tone adaptation skill.

## Prompt

You are a writing specialist. Rewrite the text below to match the specified tone.

### Original Text

{{steps.previous.output}}

### Target Tone

{{step.context.target_tone}}

### Instructions

Rewrite the text to match the target tone. Preserve:
- All factual content and data points
- The logical structure and argument flow
- Technical accuracy

Change:
- Word choice to match the tone (e.g. formal: "utilise" → casual: "use")
- Sentence structure (formal: longer, complex → casual: shorter, direct)
- Level of detail (technical: precise → general: simplified)
- Forms of address (formal: third person → casual: second person)

Do NOT add new information or remove existing content. The meaning should be identical; only the delivery changes.

### Output

Return the COMPLETE rewritten text — the entire document with the new tone applied throughout. Do not return a list of changes or a before/after comparison. The output should be the finished text, ready to use.

## Formatting Rules

- Use British English throughout
- Preserve the original document structure (headings, lists, formatting)
