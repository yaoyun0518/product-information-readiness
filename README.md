# Product Information Readiness

**Product Information Readiness is a research-driven framework and diagnostic workflow that helps merchants prepare product information for AI-driven selection and recommendation.**

**Product Information Readiness 是一套研究驱动的框架与诊断流程，帮助商户为 AI 参与商品筛选与推荐做好信息准备。**

> **Core Question｜核心问题**  
> How can product information increase the chance of being appropriately selected by AI?  
> 商品信息如何提高被 AI 正确选择与推荐的概率？

---

## Why it matters｜为什么值得做

As AI systems increasingly participate in product discovery, filtering, matching and recommendation, simply making product information available is no longer enough.

Product information can be visible to AI, yet still be difficult to understand, verify, match, or recommend with appropriate confidence.

随着 AI 越来越多地参与商品发现、筛选、匹配与推荐，仅仅“让商品信息存在”已经不够。

商品信息即使能被 AI 读取，也不代表它足够清晰、可验证、可匹配，或足以支持恰当的推荐判断。

> **The goal is not to optimize for one specific AI agent, but to help merchants prepare product information for a future where AI systems increasingly participate in product filtering, matching and recommendation.**
>
> **目标不是适配某一个具体 AI Agent，而是帮助商户提前准备好商品信息，以适应 AI 越来越多参与筛选、匹配与推荐的电商环境。**

This project focuses on the part merchants can actually influence: the quality, clarity, structure, evidence and contextual usefulness of product information.

本项目聚焦商户真正能够改善的部分：商品信息本身的质量、清晰度、结构、证据，以及在消费者语境下的可用性。

> **Platform-level access and agent permissions are external constraints and are outside the scope of this framework.**  
> **平台是否允许 Agent 访问、以及相关权限机制，属于外部约束，不在本框架的解决范围内。**

This framework focuses on what merchants can prepare in advance: product information that is easier for AI systems to understand, match, evaluate and recommend appropriately.

本框架聚焦商户可以提前准备的部分：让商品信息更容易被 AI 理解、匹配、评估，并做出恰当的推荐判断。

---

## Framework｜五维模型

Product Information Readiness currently evaluates five dimensions:

### 1. Accessibility｜信息可达性
Can AI access and read the available product information?

AI 是否能够读取现有商品信息？

### 2. Information Quality｜信息质量
Is the information accurate, current, consistent, sufficiently complete, and supported by reliable sources?

信息是否准确、及时、一致、足够完整，并有可靠来源支持？

### 3. Legibility｜信息可理解性
Can AI clearly understand what the product is, its specifications, variants, claims and usage boundaries?

AI 是否能够清楚理解商品是什么、有哪些参数、版本、卖点与使用边界？

### 4. Matchability｜需求可匹配性
Can AI map the product to real consumer needs, scenarios, constraints and preferences?

AI 是否能够把商品与真实消费者需求、场景、限制和偏好进行匹配？

### 5. Confidence｜决策信心
Is there enough relevant and reliable information for AI to include or recommend the product with appropriate confidence?

是否有足够相关且可靠的信息，让 AI 有依据地把商品纳入候选或进行推荐？

### Role Split｜维度分工

**Foundational Conditions｜基础条件**
- Accessibility
- Information Quality

**Selection Core｜选择核心**
- Legibility
- Matchability
- Confidence

---

## How it works｜如何运作

### 1. Input｜输入
Submit an existing product URL, listing page, screenshots or product materials.

提交现有商品链接、详情页、截图或商品素材。

↓

### 2. Diagnose｜诊断
Identify information conflicts, important uncertainties, and which gaps actually affect AI selection and recommendation.

识别信息冲突、关键不确定性，以及哪些缺口真正影响 AI 的筛选与推荐。

↓

### 3. Enrich｜补充
Use guided dialogue to supplement only selection-relevant information that can be supported by reliable evidence.

通过对话，只补充与选择相关、且有可靠依据的信息。

↓

### 4. Context Test｜消费者语境测试
Use merchant-provided simulated consumer contexts based on collected customer needs, purchase patterns or target audience profiles to test whether the enriched information supports appropriate AI selection decisions.

基于商户已经收集到的客户需求、购买特征或目标客群画像，构造具有代表性的消费者语境，测试当前商品信息是否足以支持 AI 做出恰当的选择判断。

↓

### 5. Re-evaluate｜重新评估
Reassess product information readiness and identify any remaining critical Unknown / Unverified items.

重新评估商品信息准备度，并检查是否仍存在关键 Unknown / Unverified。

↓

### 6. Final Listing｜最终词条
Generate a complete enriched listing that preserves verified facts, relevant limitations, usage boundaries and unresolved uncertainty.

输出完整优化后的商品词条，保留已验证事实、相关限制、使用边界与尚未解决的不确定性。

> **Behind the Skill is a tested Prompt Workflow.**  
> 这个 Skill 背后不是一条简单提示词，而是一套经过测试的判断工作流。

---

## Quick Example｜快速示例

### Watch Case｜腕表案例

**Baseline Information｜原始信息**
- 19mm watch
- 6 variants
- Fashion positioning
- Daily use

**Key Gaps｜关键缺口**
- Wrist fit unknown
- Variant differences unclear
- Water-use boundary unclear
- Formal-scenario suitability weakly supported

**After Enrichment｜补充后**
- Wrist range: 130–185mm
- Strap-material differences clarified
- Daily / commuting / date / formal scenarios clarified
- Water-use boundary clarified

**AI Judgment Change｜AI 判断变化**
- Before: insufficient information to recommend confidently
- After: conditional recommendation with stronger matching confidence

- 补充前：信息不足，无法明确推荐
- 补充后：可以进行有条件推荐，匹配判断更清楚

This case shows that selection-relevant enrichment can improve AI matching quality.

这个案例说明，与选择相关的信息补充，可以提高 AI 的匹配判断质量。

---

## Validation Cases｜验证案例

### Case 1｜Watch

**Goal:** test whether enrichment improves AI matching and recommendation readiness.

**目标：**验证补充与选择相关的信息后，AI 是否能做出更清晰的匹配与推荐判断。

Key learning:

> **Not all missing information affects AI selection and recommendation.**  
> **不是所有缺失的信息，都会影响 AI 的选择与推荐。**

Not every missing field deserves equal attention.

不是所有缺失字段都值得被同等追问。

See: [`examples/watch_case.md`](examples/watch_case.md)

---

### Case 2｜Infant Soothing Device

**Goal:** test whether the importance of an information gap changes across simulated consumer contexts.

**目标：**验证同一个信息缺口，在不同模拟消费者语境下是否会改变重要性。

Three consumer contexts were simulated based on different purchase needs:

- Light daytime white-noise use
- Overnight automatic soothing
- Content playback as the primary use

基于不同购买需求，模拟了三种消费者语境：

- 白天轻度白噪音使用
- 夜间自动安抚
- 以内容播放为主

The same cry-detection uncertainty became:

- secondary in one context,
- critical in another,
- secondary again in a third.

同一个“哭声检测可靠性”缺口，在不同场景中会从次要因素变成核心因素，再变回次要因素。

Key learning:

> **The same missing information may be critical in one consumer context and secondary in another.**  
> 同一条缺失信息，在一个消费者语境中可能是核心缺口，在另一个语境中可能只是次要信息。

This finding later informed the addition of a **Merchant-simulated Consumer Context Test｜商户模拟消费者语境测试** in the workflow.

这一发现也进一步推动了流程中 **Merchant-simulated Consumer Context Test｜商户模拟消费者语境测试** 的加入。

See: [`examples/infant_soothing_context_test.md`](examples/infant_soothing_context_test.md)

---

## Key Findings｜关键发现

- **Not all missing information affects AI selection and recommendation.**  
  **不是所有缺失的信息，都会影响 AI 的选择与推荐。**

- **Better information does not necessarily increase recommendation rate.**  
  更好的信息不一定提高推荐率。

- **The same gap can change importance across consumer contexts.**  
  同一个缺口的重要性会随着消费者语境变化。

- **Feature existence and feature reliability are different questions.**  
  功能是否存在，与功能是否可靠，是两个不同的问题。

- **Better information should improve selection quality, not merely make every product more recommendable.**  
  更好的信息应该提升选择判断质量，而不是让所有商品都更容易被推荐。

- **When critical uncertainty remains, warn rather than fabricate.**  
  当关键不确定性仍然存在时，应该提醒，而不是编造。

---

## Repository Structure｜仓库结构

```text
product-information-readiness/
├── README.md
├── model/
│   └── Product_Information_Readiness_Model_V0.3.md
├── workflow/
│   ├── Prompt_Workflow_V0.6.md
│   ├── Output_Flow_V0.4.md
│   └── README.md
├── examples/
│   ├── watch_case.md
│   └── infant_soothing_context_test.md
└── docs/
    ├── process_log.md
    └── validation_log_2026-09-25.md
```

### Where to start｜推荐阅读顺序

1. `README.md`
2. `examples/`
3. `model/`
4. `workflow/`
5. `docs/`

---

## Current Versions｜当前版本

- **Product Information Readiness Model V0.3**
- **Prompt Workflow V0.6**
- **Output Flow V0.4**

---

## Current Status｜当前状态

**Research → Insight → Framework → Tested Workflow → Skill**

This is an active research / portfolio project.

The next stage is to package the tested workflow into a reusable Skill for product-information diagnosis, enrichment and context-aware validation.

这是一个仍在持续推进中的研究型作品集项目。

下一阶段是把目前已经测试过的工作流进一步包装成可复用的 Skill，用于商品信息诊断、补充与基于消费者语境的验证。
