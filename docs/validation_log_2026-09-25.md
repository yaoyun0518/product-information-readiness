# Validation Log｜2026-09-25

## Test Goal｜测试目标

Validate whether enriched product information improves an AI system's ability to understand, match and recommend a product.

Core hypothesis:

> **Selection-relevant information matters more than generic completeness.**
> 与选择相关的信息，比单纯“信息更多”更重要。

The test compares a baseline listing with an enriched listing for the same anonymous watch product.

---

## Test Setup｜测试设置

External model: DeepSeek

Method: A/B blind-style comparison using two separate fresh conversations.

To reduce contamination from external brand knowledge, the product was anonymized as:

> **Product X｜腕表 A**

Both conversations used the same consumer need:

- Wrist size: 150mm
- Prefers a small watch face
- Main scenarios: daily commuting, dates and formal occasions
- Occasional contact with water
- No long-term swimming while wearing the watch

The model was explicitly instructed to:

- Use only the provided product information
- Not search the web
- Not rely on brand knowledge, product-category assumptions or reviews
- Mark missing information as Unknown rather than inventing facts

---

## A｜Baseline Listing

Known product information:

- Analog quartz watch
- Case diameter: 19mm
- 6 product options
- Original warranty
- Positioned as a fashion watch
- Suitable for daily wear

### DeepSeek Result

**Recommendation:** Cannot clearly recommend

**Confidence:** Low

Main reasons:

- Water resistance was unknown
- Formal-occasion suitability was not sufficiently supported
- Wrist-fit information was missing
- Differences between the six options were unknown
- Several purchase-relevant details were missing

The model could identify partial relevance, but did not have enough product information to form a stable recommendation.

---

## B｜Enriched Listing

Additional information included:

- Suitable wrist size: 130–185mm
- 3 stainless-steel Milanese strap options
- 3 nylon woven strap options
- Suitable scenarios: daily, commuting, dates, formal occasions
- Daily water resistance
- Not recommended for long-term swimming
- Approx. 30g weight, explicitly marked as an approximate value
- Original warranty

### DeepSeek Result

**Recommendation:** Tends to recommend, conditionally

**Confidence:** Medium

Main reasons:

- The user's 150mm wrist falls within the stated 130–185mm fit range
- The stated use scenarios directly overlap with the user's needs
- The water-use boundary does not conflict with the user's stated behavior
- Strap-material choices create a basis for preference matching

The model still identified unresolved questions such as precise water-resistance level, price, warranty scope and some technical specifications, so confidence did not reach High.

---

## Comparison｜对比结果

| Dimension | Baseline A | Enriched B | Change |
|---|---|---|---|
| Recommendation | Cannot clearly recommend | Conditional recommendation | Improved |
| Decision confidence | Low | Medium | Improved |
| Wrist-fit matching | Not confirmable | Directly matchable | Improved |
| Scenario matching | Weak / incomplete | Direct overlap with user scenarios | Improved |
| Water-use matching | Unknown | Boundary is usable for judgment | Improved |
| Variant-level matching | Unknown differences | Strap material differences available | Improved |

---

## Key Finding 1｜关键发现 1

> **The enriched listing moved the AI from “insufficient information to recommend” to “able to make a conditional recommendation.”**
> 优化后的商品信息，让 AI 从“信息不足，无法明确推荐”变成了“可以进行有条件推荐”。

This supports the project's core direction: product information should not merely become more complete; it should become more useful for AI selection and recommendation.

---

## Key Finding 2｜关键发现 2

The strongest improvements came from information that directly mapped to user needs:

- Wrist range → fit judgment
- Usage scenarios → scenario matching
- Water-use boundary → constraint matching
- Strap differences → preference / option matching

This supports the concept of:

> **Selection-relevant Gap Detection｜与选择相关的信息缺口识别**

Not every missing field has equal value.

---

## Key Finding 3｜关键发现 3

DeepSeek still listed many missing fields after enrichment, including items such as movement details, battery life, lug width and warranty details.

However, not all missing information is equally relevant to the current consumer's selection decision.

Therefore:

> **Missing information ≠ Selection-relevant gap.**
> 缺失信息，不等于与选择相关的信息缺口。

This reinforces the decision not to turn the workflow into a generic completeness checklist.

---

## Methodology Learning｜验证方法学习

An earlier branded test with Daniel Wellington was not sufficiently controlled because the model introduced external / remembered product information that was not provided in the test input.

Examples included:

- 3 ATM water resistance
- Case thickness
- Wrist range
- User reviews
- Additional material and maintenance information

The second test therefore introduced two controls:

1. **Product anonymization｜商品匿名化**
2. **Closed-information instruction｜封闭信息指令**

This produced a cleaner comparison and should remain the default validation method for future A/B tests.

---

# Test 2｜Storage Device Case

## Goal

Test whether the workflow can clarify attribution, uncertainty and risk in a product where the final recommendation may remain cautious even after enrichment.

The product was an anonymized 2.5-inch mechanical external drive using a hard-drive enclosure plus a third-party drive mechanism.

Consumer need was intentionally vague:

> I want a portable drive mainly for photos, videos and everyday files. I want it to be convenient to use and easy to carry around.

### Observation

The first A/B setup produced only a small difference because the baseline already contained many of the critical facts later surfaced through the workflow, including:

- Third-party mechanical drive mechanism
- Random brand / model / new-used status
- Possible older or recycled storage media
- Need for multiple backups
- No data-recovery service

This meant the comparison was closer to:

> **Original information, already heavily整理ed → structured attribution version**

rather than a clean:

> **Original listing → Enriched listing**

### Method Adjustment

This case should not be treated as a strong A/B efficacy result.

Its main valid learning was:

> **Structured attribution improves reasoning clarity, even when the final recommendation does not change.**
> 即使最终推荐结论不变，更清晰的信息归属仍然能让 AI 的判断逻辑更准确。

Examples:

- “<500MB/s” was clarified as an enclosure/interface upper-bound description rather than guaranteed real drive speed.
- Waterproof / dustproof / drop-protection claims were separated from verified test evidence.
- A simulated 400MB/s merchant input was explicitly marked as simulated rather than original verified listing data.

---

# Test 3｜Readiness Warning Validation

## Goal

Validate when the workflow should stop repetitive questioning and trigger a **Readiness Warning｜信息准备度提醒**.

The same storage-device case was used because several core reliability factors were uncertain.

### Merchant answers during guided dialogue

The merchant could not confirm:

- Drive brand
- Drive model
- Whether the drive was new, old stock, removed from another device, or refurbished
- A verifiable test report / health report

These were not peripheral fields. They directly affected reliability, lifespan, performance and recommendation confidence.

### Trigger Decision

The workflow did **not** trigger a warning after the first Unknown.

It continued until uncertainty formed a cluster across several related **Core Decision Factors｜核心决策因素**.

At that point, the correct behavior was:

1. Stop repetitive questioning.
2. Trigger a **High-Uncertainty Warning｜高不确定性提醒**.
3. Keep unresolved items explicitly marked Unknown / Unverifiable.
4. Avoid inventing or pressuring the merchant to guess.
5. Recommend source-level next steps such as supplier documents, SMART / health diagnostics, or test reports.
6. Allow the workflow to continue using known information, while keeping **Confidence｜决策信心** appropriately low.

### Validated Warning Pattern

> **当前商品存在较高的信息不确定性。**  
> 即使页面信息较完整，AI 仍可能因为关键事实无法验证而降低推荐信心。  
> 建议先补充核心来源信息，再继续优化商品词条。

### Key Finding 4｜关键发现 4

> **Readiness Warning should be triggered by clustered selection-relevant uncertainty, not by raw missing-field count.**
> 信息准备度提醒应由“成片出现的选择相关不确定性”触发，而不是由缺失字段数量触发。

This validated the V0.5 trigger boundary:

- One Unknown is not enough.
- Several related Core Decision Factors remaining Unknown / Unverifiable can justify a warning.
- Once the problem becomes source-level rather than copy-level, continued wording optimization should not be treated as the solution.

---

# Test 4｜Infant Soothing Device + Consumer Context Shift

## Goal

Validate two questions:

1. Does enriched information always increase recommendation confidence?
2. Does the importance of an information gap change when the consumer context changes?

The product was anonymized as:

> **Product Z｜婴幼儿安抚仪**

The enriched version clarified:
- Cry detection must be manually enabled.
- When enabled, it detects crying in real time and automatically plays white noise.
- Timer ends playback after 30 / 60 / 90 minutes.
- Page-stated endurance is about 58 hours, but test conditions are unknown.
- Suggested placement distance is unknown.
- 37–80 dB test distance / conditions / source are unknown.
- Cry-detection sensitivity, recognition distance and false-trigger behavior are unknown.
- CE and CAN ICES marks exist, but cannot be treated as proof of infant-material safety.

## Initial A/B result

Under a general soothing / night-use consumer need:

- Baseline A: conditional / pending candidate, Confidence Low
- Enriched B: conditional / pending candidate, Confidence Low

The final confidence did not increase.

However, B's reasoning became more focused:
- A was cautious because many details were simply missing.
- B was cautious because specific, selection-relevant uncertainties remained around sound-use boundaries, cry-detection reliability, endurance conditions and infant-use evidence.

### Key Finding 5｜关键发现 5

> **Better information does not necessarily increase recommendation rate or confidence.**
> 更好的信息不一定提高推荐率或推荐信心。

A better outcome can also be a more precise reason for caution.

Therefore:

> **Better product information should improve selection quality, not merely increase recommendation rate.**
> 更好的商品信息应该提升 AI 的选择判断质量，而不是机械地提高推荐率。

---

## Context Shift Test｜消费者语境切换测试

Product information was held constant. Only the consumer context changed.

Three contexts were tested with both Baseline A and Enriched B.

### Context 1｜Light daytime use

Consumer mainly wanted occasional daytime white noise, home use plus some portability, and did not depend on automatic soothing.

Results:
- A1: conditional candidate, Confidence Low
- B1: conditional candidate, Confidence Medium

Important behavior:
- In B1, cry-detection sensitivity / range / false-trigger uncertainty was explicitly treated as relatively unimportant because automatic soothing was not a core need.
- The model instead focused more on white-noise availability, timer, Type-C charging, portability, operation and sound-use boundaries.

### Context 2｜Overnight automatic soothing

Consumer wanted a newborn to use the device at night for long periods and relied on automatic cry recognition and soothing.

Results:
- A2: not ready for recommendation / needs key information, Confidence Low
- B2: not ready for recommendation / needs key information, Confidence Low

Important behavior:
- A2 could not confirm whether “supports cry detection” actually meant cry-triggered automatic soothing.
- B2 resolved the feature-existence question and moved deeper into feature-reliability questions:
  - sensitivity,
  - recognition distance,
  - false triggers,
  - playback behavior after triggering,
  - sound-use distance,
  - volume-test conditions,
  - endurance conditions,
  - infant-use safety evidence.

This revealed a useful progression:

> **Feature existence uncertainty → Feature reliability uncertainty**

### Context 3｜Content playback as primary use

Consumer mainly cared about songs, stories, white noise, occasional parent-voice recording, endurance and portability. Automatic soothing was secondary.

Results:
- A3: pending candidate, Confidence Low
- B3: conditional candidate, Confidence Low

Important behavior:
- Cry-detection unknowns were correctly downgraded to secondary.
- The main remaining gaps shifted toward operation, content usability, recording details, real endurance conditions and portability.

---

## Key Finding 6｜关键发现 6

> **The same missing information may be critical in one consumer context and secondary in another.**
> 同一条缺失信息，在一个消费者语境中可能是核心缺口，在另一个语境中可能只是次要信息。

Cry-detection reliability was the clearest example:
- Secondary in light daytime use
- Critical in overnight automatic soothing
- Secondary again in content-playback use

This supports **Dynamic Decision Context｜动态决策语境** as a formal workflow requirement.

---

## Key Finding 7｜关键发现 7

The context-shift test also showed that enriched information can improve confidence selectively rather than universally.

Only B1 moved from Low to Medium confidence.

B2 stayed Low because the consumer context made unresolved safety and reliability gaps critical.

B3 stayed Low because several consumer-priority details — operation, content usability, recording details and real endurance conditions — were still unresolved.

Therefore:

> **Context determines which Unknowns matter, and which Unknowns can safely remain secondary.**
> 消费者语境决定哪些 Unknown 真正影响选择，以及哪些 Unknown 可以保持次要。

---

## Workflow Implication｜流程影响

The validation results led to a new workflow step:

### Merchant Context Test｜商户消费者语境测试

After first-round enrichment, the merchant provides 2–3 real, high-frequency consumer contexts based on their customer knowledge.

For each context, the workflow checks whether the enriched listing supports an appropriate AI selection decision.

If important context-specific gaps remain, the merchant is asked whether to continue into another enrichment round.

If the merchant chooses not to continue, the workflow preserves the first-round enrichment result and keeps unresolved Unknown / Unverified items explicit.

This became part of **Prompt Workflow V0.6** and **Output Flow V0.4**.

---

## Validation Status｜当前验证状态

Current evidence is **directionally supportive, not conclusive**.

What is supported so far:

- Selection-relevant enrichment can improve AI matching and recommendation confidence.
- Missing information and selection-relevant gaps are not the same thing.
- Structured attribution can improve reasoning clarity even when the recommendation itself does not change.
- Readiness Warnings are useful when core uncertainty becomes clustered and source-level.
- Better information does not always increase recommendation confidence; it can also produce better-calibrated caution.
- The same information gap can change importance across consumer contexts.
- Context-aware validation can reveal whether first-round enrichment is actually sufficient for real customer scenarios.

What still needs more evidence:

- Whether context-dependent gap weighting reproduces consistently across more product categories.
- Whether different external AI models respond similarly.
- Whether merchant-supplied consumer contexts produce stable and useful second-round enrichment priorities.
- Whether the current Warning trigger remains appropriate across categories with different risk profiles.
