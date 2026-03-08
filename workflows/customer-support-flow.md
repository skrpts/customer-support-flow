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
