# Product Information Readiness

A research-driven framework and workflow for improving product information readiness for AI selection and recommendation.

> **Core question**  
> How can product information increase the chance of being appropriately selected by AI?

## Why this project

As AI agents increasingly participate in product discovery and recommendation, simply making product information available is not enough.

The more useful question is whether AI can:
- access the information,
- understand it correctly,
- match it to real consumer needs,
- and make a context-appropriate recommendation.

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

**Input → Extract → Identify → Conflict Check → Five-Dimension Evaluation → Dynamic Decision Context → Selection-relevant Gap Detection → Conversational Enrichment → Readiness Warning → Re-evaluate → Merchant Context Test → Context Gap Check → Continue? → User Confirmation → Final Enriched Listing**

Rather than using a fixed checklist, the workflow dynamically identifies which information actually affects AI filtering, matching, and recommendation for a specific product and consumer context.

If multiple selection-critical facts remain Unknown or Unverifiable after enrichment, the workflow triggers a **Readiness Warning** instead of pushing the merchant to fill gaps by guessing.

After first-round enrichment, the merchant can provide 2–3 real, high-frequency consumer contexts. The workflow tests the enriched listing against those contexts, checks whether any selection-relevant gaps remain, and asks whether the merchant wants to enter another enrichment round.

## Example cases

Two public examples illustrate different parts of the framework.

### Case 1｜Watch — enrichment and conditional recommendation

This case compares a baseline watch listing with an enriched version under the same consumer need.

The enriched listing added selection-relevant information such as:
- wrist-fit range,
- usage scenarios,
- water-use boundaries,
- and variant differences.

The external AI moved from insufficient information to a conditional recommendation, while confidence remained calibrated rather than becoming automatically high.

**What this case demonstrates:**

> Better information can improve matching and recommendation quality without guaranteeing a strong recommendation.

See: [`examples/watch_case.md`](examples/watch_case.md)

### Case 2｜Infant soothing device — consumer context shift

This case holds product information constant while changing the consumer scenario.

The same unknown — cry-detection reliability — became:
- secondary for light daytime white-noise use,
- critical for overnight automatic soothing,
- secondary again when content playback was the main purchase reason.

**What this case demonstrates:**

> The importance of an information gap changes with consumer context.

It also motivated the addition of **Merchant Context Test｜商户消费者语境测试** to the workflow.

See: [`examples/infant_soothing_context_test.md`](examples/infant_soothing_context_test.md)

Together, the two cases support a broader conclusion:

> **Better product information should improve the quality of AI selection, not merely increase recommendation rate.**

## Key principles

- **Low input burden, high diagnostic value.**
- **Single-product evaluation only.**
- Resolve conflicts before filling gaps.
- Do not optimize completeness at the expense of truthfulness.
- Evidence should support the exact claim, not a broader interpretation.
- Verification status is discovered through dialogue rather than assumed in advance.
- Human trust and AI confidence are not the same thing.
- Missing information is not automatically a selection-relevant gap.
- The same missing information can be critical in one consumer context and secondary in another.
- Better information should improve selection quality, not merely increase recommendation rate.
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
- infant soothing devices

Current validation focuses on whether the workflow improves AI understanding, matching, recommendation boundaries, and context-appropriate confidence. External AI blind testing is used to compare baseline and enriched product information.

Recent context-shift testing also keeps product information fixed while changing the consumer scenario, to observe whether AI appropriately changes which gaps matter most.

## Current versions

- **Product Information Readiness Model V0.3**
- **Prompt Workflow V0.6**
- **Output Flow V0.4**

## Project direction

**Research → Insight → Framework → Tested Workflow → Skill**

The long-term goal is to package this workflow into a reusable Skill that helps merchants evaluate and improve existing product information before and after publishing.

After publishing, the product detail page can be submitted again for re-evaluation to check whether any information gaps still affect AI selection and recommendation.

---

**Status:** Active research / portfolio project
