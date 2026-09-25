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

## Validation Status｜当前验证状态

Current evidence is **directionally supportive, not conclusive**.

What is supported so far:

- Selection-relevant enrichment can improve AI matching and recommendation confidence.
- Missing information and selection-relevant gaps are not the same thing.
- Structured attribution can improve reasoning clarity even when the recommendation itself does not change.
- Readiness Warnings are useful when core uncertainty becomes clustered and source-level.

What still needs more evidence:

- Whether the matching/confidence improvement reproduces consistently across more product categories.
- Whether different external AI models respond similarly.
- Whether the current Warning trigger remains appropriate across categories with different risk profiles.
