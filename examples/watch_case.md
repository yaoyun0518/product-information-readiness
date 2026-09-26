# Example 1｜Watch Case

## Why this case matters

This case tests whether enriching product information can improve AI matching and recommendation readiness.

It also demonstrates an important boundary:

> **More complete information can improve matching without guaranteeing a high-confidence recommendation.**
> 信息补充可以提升匹配质量，但并不保证 AI 一定会高信心推荐。

## Product setup

The product was anonymized as:

> **Product X｜腕表 A**

The external model was instructed to use only the provided product information, avoid web search and brand knowledge, and mark missing information as Unknown.

## Consumer need

- Wrist size: 150 mm
- Prefers a small watch face
- Main scenarios: daily commuting, dates and formal occasions
- Occasional contact with water
- No long-term swimming while wearing the watch

## A｜Baseline information

- Analog quartz watch
- Case diameter: 19 mm
- 6 product options
- Original warranty
- Positioned as a fashion watch
- Suitable for daily wear

### AI result

- Recommendation: cannot clearly recommend
- Confidence: Low

Main gaps:
- Wrist-fit range unknown
- Water-use boundary unclear
- Formal-occasion suitability not sufficiently supported
- Differences between product options unknown

## B｜Enriched information

Additional verified / clarified information:

- Suitable wrist size: 130–185 mm
- 3 stainless-steel Milanese strap options
- 3 nylon woven strap options
- Suitable scenarios: daily, commuting, dates, formal occasions
- Daily water resistance
- Not recommended for long-term swimming
- Approx. 30 g weight

### AI result

- Recommendation: conditional recommendation
- Confidence: Medium

The model could now directly match:
- 150 mm wrist → 130–185 mm fit range
- commuting / dates / formal occasions → stated use scenarios
- occasional water contact → stated water-use boundary
- strap differences → preference matching

However, several details still remained unresolved, so the enriched listing did not become a high-confidence recommendation.

## What this case validates

### 1. Selection-relevant enrichment matters

The most useful additions were not generic completeness fields. They were the facts that directly mapped to the consumer's needs.

> **Not all missing information affects AI selection and recommendation.**
> 不是所有缺失的信息，都会影响 AI 的选择与推荐。

### 2. Enrichment does not guarantee high recommendation confidence

The goal is not to make the product look more recommendable at all costs.

A better listing should help AI make a more grounded decision, which may still remain conditional when meaningful uncertainty remains.

### 3. Matching quality can improve even when uncertainty remains

This case supports the idea that Product Information Readiness should be evaluated by decision quality, not only by whether the recommendation score or confidence rises.

## Key takeaway

> **Better product information can move AI from “insufficient information” to a more precise, conditional selection decision — but it should not force certainty where evidence is still incomplete.**
