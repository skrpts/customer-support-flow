---
type: workflow
id: customer-support-flow
title: Customer Support Flow
description: "Classifies customer intent and drafts an appropriate response"
tags: [Production, Communication, Automation]
connections:
  - target: intent-classification
    type: uses
  - target: response-drafting
    type: uses
  - target: tone-adaptation
    type: uses
  - target: structured-data-extraction
    type: uses
  - target: llm-service
    type: runs_on
  - target: brand-guidelines
    type: references
  - target: customer-tone-guide
    type: references
  - target: company-style-guide
    type: references
  - target: language-polish
    type: uses
  - target: format-conversion
    type: uses
  - target: pii-masking
    type: uses
output_step: "language-polish"
composite_steps:
  - "intent-classification"
  - "response-drafting"
  - "tone-adaptation"
  - "structured-data-extraction"
  - "format-conversion"
  - "pii-masking"
execution:
  - skill: "intent-classification"
    step_type: "synthesis"
    prompt: "classify-intent"
    output: { name: "intent", type: "text" }
  - skill: "response-drafting"
    prompt: "customer-response-draft"
    step_type: "generation"
    output: { name: "draft_response", type: "text" }
  - skill: "tone-adaptation"
    prompt: "adapt-tone"
    step_type: "content"
    output: { name: "toned_response", type: "text" }
    context:
      target_tone: "Professional and approachable"
  - skill: "language-polish"
    prompt: "polish-language"
    step_type: "content"
    output: { name: "polished_response", type: "text" }
    context:
      voice_profile: "Neutral professional tone"
      grammar_strictness: "Professional"
  - skill: "structured-data-extraction"
    prompt: "extract-structured-data"
    step_type: "synthesis"
    output: { name: "structured_data", type: "json" }
    context:
      extraction_fields: "Key findings, dates, names, action items"
  - skill: "format-conversion"
    step_type: "local.transform"
    output: { name: "formatted_response", type: "text" }
  - skill: "pii-masking"
    step_type: "local.transform"
    output: { name: "masked_response", type: "text" }
---

## Overview

This workflow processes incoming customer messages by first classifying the intent, then drafting an appropriate response based on the detected intent and company tone guidelines.

## Pipeline Stages

### Stage 1: Classify Intent

Invoke the **intent-classification** skill to analyse the customer message and determine whether it is a question, request, complaint, feedback, or other.

### Stage 2: Draft Response

Invoke the **response-drafting** skill using the classified intent and customer tone guide to generate an empathetic, on-brand response ready for human review.

### Stage 3: Language Polish

Surface-level cleanup: spelling, grammar, punctuation, and sentence clarity on the drafted response.

### Stage 4: Data Extraction

Extract structured data from the conversation: key findings, dates, names, and action items for CRM logging.

### Stage 5: Format Conversion + PII Masking

Convert the output to the required format and mask any personally identifiable information before storage or handoff.

## Output

A draft customer response containing:

- Acknowledgement of the customer's concern
- Direct response addressing the specific intent
- Clear next steps
- Professional tone matching company guidelines

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.customer_message}}` | Yes | The customer's message text to classify and respond to | "I've been waiting 3 days for my order and still no tracking number" |

## Outputs

| Name | Description |
|------|-------------|
| Classified intent | The detected intent category (question, request, complaint, feedback, other) |
| Draft response | An empathetic, on-brand response ready for human review |

## Setup

Before running this workflow:

1. **Paste the customer message** — no external services or integrations are required. Simply provide the customer's message text.

No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Works well with any model — no specific provider requirements
- All common LLMs handle intent classification and response drafting effectively

## Example Input

To test this workflow immediately after import:

```
Customer message: "Hi, I ordered a laptop case last week and it arrived damaged. The zipper is broken and there's a tear on the side. I'd like a replacement or a refund please."
```
