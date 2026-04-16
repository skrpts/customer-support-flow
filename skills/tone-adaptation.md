---
type: skill
id: tone-adaptation
title: Tone Adaptation
description: "Rewrites text to match a specified tone whilst preserving meaning"
tags: [Tested, Communication, Automation]
context_params:
  target_tone:
    label: "Target Tone"
    description: "The desired tone for the output"
    default: "Professional and approachable"
    required: false
connections:
  - target: llm-service
    type: runs_on
  - target: customer-tone-guide
    type: references
  - target: brand-guidelines
    type: references
---

## Capability

Rewrites text to match a specified tone (formal, casual, empathetic, technical) while preserving meaning.

## When to Use

- Adapting internal docs for customer-facing use
- Adjusting email tone for different audiences
- Making technical content accessible

## Inputs

Original text + target tone description

## Outputs

Rewritten text matching the target tone, all facts preserved
