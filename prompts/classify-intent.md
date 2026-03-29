---
type: prompt
id: classify-intent
title: Classify Intent
description: "Core prompt for classifying customer message intent"
tags: [Production, utility:classification, writing:communication]
connections:
  - target: intent-classification
    type: derived_from
---

## Purpose

Classifies incoming customer messages into intent categories with a confidence score, enabling automated routing and response selection.

## Prompt

You are a customer support intent classifier.

Analyse the following user message and classify its intent into one of these categories:
- **question** — asking for information
- **request** — asking for an action to be taken
- **complaint** — expressing dissatisfaction
- **feedback** — providing a suggestion or opinion
- **other** — does not fit the above

Return a JSON object with `intent` (string) and `confidence` (0-1).

## User Message

{{input.customer_message}}
