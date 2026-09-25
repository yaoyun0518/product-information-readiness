# Project 02 Process Log

## Project Direction

Project 02 started from Agentic Commerce and the broader question:

> How can a brand become understandable, selectable and trustworthy to AI agents?

The project later narrowed from **Brand Information Readiness** to **Product Information Readiness**, focusing on a specific product listing rather than brand-wide consistency.

## Key Turning Points

### 1. From readability to selection
Early exploration focused on whether AI could access and understand product information. Real listing tests suggested many listings were already readable enough when materials were available.

The central question shifted to:

> **How can product information increase the chance of being selected by AI?**

### 2. Fixed checklist rejected
A static field-completion checklist was considered too rigid across categories.

The project adopted dynamic judgment based on:
- Product category
- Hard constraints
- Real buying context
- Evidence quality
- Remaining uncertainty

### 3. Human Trust ≠ AI Confidence
Consumer trust signals such as awards and media exposure may improve human persuasion, but AI recommendation confidence depends more on whether claims are specific, attributable, relevant and sufficiently supported.

### 4. Conflict detection became a formal step
Real product tests revealed that conflicting specifications can be more damaging than missing fields.

**Conflict Check｜冲突检查** was therefore added before gap detection.

### 5. Information Quality retained as a core dimension
Information quality was not treated as a horizontal note. Accuracy, freshness, consistency, completeness and source reliability remain part of the five-dimensional model.

### 6. Category-specific confidence
Confidence should reflect what reduces uncertainty in that category rather than applying one universal evidence standard.

### 7. Evidence cannot be broadened
If a source supports “jogging,” it does not automatically support “long-distance running.”

### 8. Truthfulness over completeness
The workflow should never pressure a merchant to invent information simply to make the listing look more complete.

### 9. Conversational Enrichment
The interaction model evolved from “show all missing fields” to asking one useful question at a time.

### 10. Service information deprioritized
Operational/service details are secondary unless they materially affect initial discovery, filtering or recommendation.

### 11. Verification status is discovered through dialogue
Whether reliable source material exists cannot always be known upfront. Verification status therefore emerges during the interaction rather than serving as an initial input.

### 12. Missing information ≠ selection-relevant gap
Blind testing showed that an AI can list many missing fields that do not materially affect the current consumer's decision.

This led to a sharper distinction between generic completeness and information that actually affects filtering, matching and recommendation.

### 13. Better information does not always increase recommendation confidence
Tests with higher-risk products showed that better information can make AI more cautious rather than more favorable.

A more mature interpretation emerged:

> **Better product information should improve selection quality, not merely increase recommendation rate.**

The result of better information may be:
- stronger recommendation,
- unchanged but better-calibrated confidence,
- clearer conditional recommendation,
- or clearer exclusion.

### 14. Selection-relevant gaps are context-dependent
A context-shift test on an infant soothing device kept the product information fixed while changing the consumer scenario.

The same unknown — such as cry-detection reliability — became:
- secondary for light daytime white-noise use,
- critical for overnight automatic soothing,
- secondary again when content playback was the main purchase reason.

This validated:

> **The importance of an information gap changes with consumer context.**
> 同一条信息缺口的重要性，会随着消费者语境改变。

### 15. Feature existence and feature reliability are different questions
In the baseline infant-soother test, the AI could only ask whether cry detection actually triggered automatic soothing.

After enrichment, that question was resolved, allowing the AI to move deeper into:
- sensitivity,
- recognition distance,
- false triggering,
- usage boundaries,
- and safety-related uncertainty.

This revealed a useful distinction:

> **Feature existence uncertainty → Feature reliability uncertainty**

### 16. Merchant Context Test added
Because merchants often understand their real customer groups better than a generic test prompt, the workflow now asks them to provide 2–3 high-frequency consumer contexts after first-round enrichment.

Each context should describe:
- who the consumer is,
- why they buy,
- what matters most,
- hard constraints,
- secondary / nice-to-have factors.

The merchant should provide real demand, not instructions for how they want AI to recommend the product.

### 17. Context validation becomes iterative
If the AI finds that the enriched listing is still insufficient or inaccurate in an important merchant-supplied consumer context, the workflow asks whether the merchant wants another enrichment round.

If yes:

**Enrich → Re-evaluate → Merchant Context Test → Context Gap Check**

If no:
- stop iteration,
- preserve the first-round confirmed enrichment result,
- retain unresolved Unknown / Unverified items,
- keep any relevant Readiness Warning.

This prevents endless questioning while allowing useful second-round refinement.

## Current Public Narrative

**Research → Insight → Framework → Tool**

Potential portfolio framing:

> I entered an unfamiliar and fast-changing field, built a clear research framework, identified a meaningful product-information problem, and translated it into a practical strategic tool.

A stronger current interpretation of the project is:

> The tool is not designed to make every product more recommendable. It is designed to help AI make better, more context-appropriate selection decisions from product information.

## Publication Plan

- **Post 1**: demonstrate the finished Skill / workflow result
- **Post 2**: show the research process, rejected concepts, framework changes and decision logic

A useful line for the public-facing Skill:

> **Behind the Skill is a tested Prompt Workflow.**
