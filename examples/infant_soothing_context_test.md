# Example 2｜Infant Soothing Device Context Test

## Why this case matters

This case tests a different question from the watch example:

> **Does the importance of an information gap change when the consumer context changes?**
> 同一条信息缺口的重要性，会不会随着消费者语境改变？

The product information was kept constant. Only the consumer scenario changed.

## Product setup

The product was anonymized as:

> **Product Z｜婴幼儿安抚仪**

The enriched listing clarified:
- Cry detection must be manually enabled
- When enabled, it detects crying in real time and automatically plays white noise
- 30 / 60 / 90 minute timer; playback stops when time ends
- Page-stated endurance: about 58 hours
- 15 volume levels
- Page-stated volume range: 37–80 dB
- Type-C charging
- CE and CAN ICES markings exist

Important remaining Unknowns included:
- Recommended placement distance
- Volume-test distance / conditions / source
- Cry-detection sensitivity
- Recognition distance
- False-trigger behavior
- Endurance test conditions
- More specific infant-material safety evidence

## Context 1｜Light daytime use

Consumer mainly wanted occasional daytime white noise, mainly at home, with some portability. Automatic soothing was not important.

### Result

- Baseline A: conditional candidate, Confidence Low
- Enriched B: conditional candidate, Confidence Medium

### What changed

Cry-detection sensitivity / range / false-trigger uncertainty became relatively unimportant because automatic soothing was not part of the consumer's core need.

The AI instead focused on:
- white-noise availability
- timer
- Type-C charging
- portability
- operation
- sound-use boundaries

## Context 2｜Overnight automatic soothing

Consumer wanted the device for a newborn at night and specifically relied on automatic cry recognition and soothing.

### Result

- Baseline A: needs key information, Confidence Low
- Enriched B: needs key information, Confidence Low

### What changed

In the baseline, the AI could not even confirm whether “supports cry detection” meant cry-triggered automatic soothing.

After enrichment, that feature-existence question was resolved.

The AI then moved deeper into reliability questions:
- sensitivity
- recognition distance
- false triggers
- playback behavior after triggering
- sound-use distance
- volume-test conditions
- endurance conditions
- infant-use safety evidence

This produced a useful distinction:

> **Feature existence uncertainty → Feature reliability uncertainty**

## Context 3｜Content playback as primary use

Consumer mainly cared about songs, stories, white noise, occasional parent-voice recording, endurance and portability. Automatic soothing was secondary.

### Result

- Baseline A: pending candidate, Confidence Low
- Enriched B: conditional candidate, Confidence Low

### What changed

Cry-detection uncertainty became secondary again.

The AI shifted attention toward:
- operation
- content usability
- recording details
- real endurance conditions
- portability

## What this case validates

### 1. Selection-relevant gaps are context-dependent

> **The same missing information may be critical in one consumer context and secondary in another.**
> 同一条缺失信息，在一个消费者语境中可能是核心缺口，在另一个语境中可能只是次要信息。

Cry-detection reliability is the clearest example:
- Secondary in light daytime use
- Critical in overnight automatic soothing
- Secondary again in content-playback use

### 2. Better information does not always increase recommendation confidence

Only the light-use enriched case moved from Low to Medium confidence.

The overnight-use case correctly stayed Low because unresolved safety and reliability gaps were central to the consumer need.

The content-playback case also stayed Low because several consumer-priority details were still unresolved.

### 3. Consumer context should be part of validation

This case led to the addition of:

> **Merchant Context Test｜商户消费者语境测试**

After first-round enrichment, merchants provide 2–3 real, high-frequency consumer contexts based on their actual customer knowledge.

The workflow then checks whether the enriched listing supports appropriate AI selection decisions in those contexts.

## Key takeaway

> **Better information should improve selection quality, not merely increase recommendation rate.**
> 更好的商品信息应该提升 AI 的选择判断质量，而不是机械地提高推荐率。
