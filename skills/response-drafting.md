---
type: skill
id: response-drafting
title: Response Drafting
description: "Generates empathetic, on-brand responses to customer enquiries"
tags: [Tested, utility:classification, writing:communication]
connections:
  - target: llm-service
    type: runs_on
  - target: customer-tone-guide
    type: references
  - target: brand-guidelines
    type: references
---

## Capability

Generates empathetic, on-brand responses to customer enquiries, complaints, and requests based on the detected intent and company tone guidelines.

## When to Use

- Responding to inbound customer support messages
- Drafting follow-up emails after complaints
- Creating first-response templates for common enquiry types

## Inputs

Customer message + detected intent + tone guidelines

## Outputs

Draft response ready for human review, matching brand voice and addressing the customer's specific concern
