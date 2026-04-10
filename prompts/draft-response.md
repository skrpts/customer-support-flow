---
type: prompt
id: draft-response
title: "Draft Response"
description: "Drafts a customer-facing response based on intent classification and extracted details"
tags: [Production, Communication]
connections:
  - target: response-drafting
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Drives the response drafting skill.

## Prompt

You are a customer support specialist. Draft a response based on the classified intent and extracted details below.

### Classification and Details

{{steps.previous.output}}

### Instructions

1. **Acknowledge** the customer's issue or question specifically — show you understood what they reported
2. **Address** the core concern with a clear, helpful answer or next step
3. **Provide** any relevant context (known issues, timelines, workarounds)
4. **Close** with a clear next action — what happens next, and when they can expect a follow-up if needed

### Rules

- Be empathetic but concise — respect the customer's time
- Use plain language — no internal jargon or ticket numbers
- If the issue requires escalation, say so directly with an expected timeline
- Match the formality to the channel (email: more formal, chat: more conversational)

## Formatting Rules

- Use British English throughout
- Be specific and actionable — no vague recommendations
- Structure output clearly with headings, tables, or lists as appropriate
