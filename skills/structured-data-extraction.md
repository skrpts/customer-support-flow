---
type: skill
id: structured-data-extraction
title: Structured Data Extraction
description: "Extracts structured fields and data points from unstructured text"
tags: [Tested]
connections:
  - target: llm-service
    type: runs_on
---

## Capability

Extracts structured fields and key-value pairs from unstructured customer messages, including order numbers, product names, dates, and issue descriptions.

## When to Use

- Parsing customer messages for key details (order IDs, product names, dates)
- Structuring complaint data for routing and tracking
- Extracting actionable information from freeform support tickets

## Inputs

Unstructured customer message or support ticket text

## Outputs

Structured key-value pairs: customer details, issue category, referenced products/orders, dates mentioned
