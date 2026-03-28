---
type: workflow
id: customer-support-flow
title: Customer Support Flow
description: "Classifies customer intent and drafts an appropriate response"
tags: [Production]
connections:
  - target: intent-classification
    type: uses
  - target: response-drafting
    type: uses
  - target: classify-intent
    type: uses
  - target: customer-response-draft
    type: uses
  - target: tone-adaptation
    type: uses
  - target: structured-data-extraction
    type: uses
---

## Overview

This workflow processes incoming customer messages by first classifying the intent, then drafting an appropriate response based on the detected intent and company tone guidelines.

## Pipeline Stages

### Stage 1: Classify Intent

Invoke the **intent-classification** skill to analyse the customer message and determine whether it is a question, request, complaint, feedback, or other.

### Stage 2: Draft Response

Invoke the **response-drafting** skill using the classified intent and customer tone guide to generate an empathetic, on-brand response ready for human review.

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
