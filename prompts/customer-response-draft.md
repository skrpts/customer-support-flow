---
type: prompt
id: customer-response-draft
title: Customer Response Draft
description: "Task prompt for drafting professional customer support responses"
tags: [Production, Communication, Automation]
inputs:
  customer_message:
    label: "Customer Message"
    description: "The customer message or support ticket to respond to"
    example: "[Paste the customer email or message here]"
    required: true
    type: text
connections:
  - target: intent-classification
    type: derived_from
  - target: response-drafting
    type: derived_from
  - target: customer-tone-guide
    type: references
---

## Purpose

Drafts a professional, empathetic response to a customer message based on the detected intent and company tone guidelines.

## Prompt

You are a customer support agent. Draft a professional, empathetic response to the customer message below.

## Guidelines

- Match the company tone described in the tone guide
- Address the customer's concern directly based on the detected intent
- Provide clear next steps
- Keep the response concise (under 200 words)

## Tone Guide

Refer to the attached tone guide for voice and style guidance.

## Detected Intent

{{steps.previous.output}}

## Customer Message

{{input.customer_message}}

## Your Response
