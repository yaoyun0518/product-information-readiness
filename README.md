# Product Information Readiness

A research-driven framework and workflow for improving product information readiness for AI selection and recommendation.

> **Core question**  
> How can product information increase the chance of being selected by AI?

## Why this project

As AI agents increasingly participate in product discovery and recommendation, simply making product information available is not enough.

The more useful question is whether AI can:
- access the information,
- understand it correctly,
- match it to real consumer needs,
- and make a confident recommendation.

This project explores that problem through real product listings, iterative testing, and a structured diagnostic workflow.

## Framework

The current Product Information Readiness model evaluates five dimensions:

1. **Accessibility** — Can AI access and read the information?
2. **Information Quality** — Is the information accurate, current, consistent, complete enough, and free from harmful conflicts?
3. **Legibility** — Can AI clearly understand the product, its attributes, specifications, and claims?
4. **Matchability** — Can AI map the product to real needs, scenarios, users, and constraints?
5. **Confidence** — Is there enough relevant and reliable information for AI to include or recommend the product with confidence?

The first two dimensions act as foundational conditions. The last three form the core of selection readiness.

## Workflow

The tested workflow currently follows this sequence:

**Input → Extract → Identify → Conflict Check → Five-Dimension Evaluation → Dynamic Decision Context → Selection-relevant Gap Detection → Conversational Enrichment → Readiness Warning → Re-evaluate → User Confirmation → Final Enriched Listing**

Rather than using a fixed checklist, the workflow dynamically identifies which information actually affects AI filtering, matching, and recommendation for a specific product.

If multiple selection-critical facts remain Unknown or Unverifiable after enrichment, the workflow now triggers a **Readiness Warning** instead of pushing the merchant to fill gaps by guessing.

## Key principles

- **Low input burden, high diagnostic value.**
- **Single-product evaluation only.**
- Resolve conflicts before filling gaps.
- Do not optimize completeness at the expense of truthfulness.
- Evidence should support the exact claim, not a broader interpretation.
- Verification status is discovered through dialogue rather than assumed in advance.
- Human trust and AI confidence are not the same thing.
- Missing information is not automatically a selection-relevant gap.
- When critical uncertainty remains, warn rather than fabricate.

## Validation approach

The framework has been tested across multiple product categories, including:

- portable SSDs
- sunscreen
- live plants
- furniture
- food
- running shoes
- watches / accessories
- portable hard drives

Current validation focuses on whether the workflow improves AI understanding, matching, and recommendation readiness. External AI blind testing is now being used to compare baseline and enriched product information.

## Current versions

- **Product Information Readiness Model V0.3**
- **Prompt Workflow V0.5**
- **Output Flow V0.3**

## Project direction

**Research → Insight → Framework → Tested Workflow → Skill**

The long-term goal is to package this workflow into a reusable Skill that helps merchants evaluate and improve existing product information before and after publishing.

After publishing, the product detail page can be submitted again for re-evaluation to check whether any information gaps still affect AI selection and recommendation.

---

**Status:** Active research / portfolio project
