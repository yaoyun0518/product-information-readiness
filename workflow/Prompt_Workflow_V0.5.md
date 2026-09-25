# Prompt Workflow V0.5｜选择优化版

## 0. Core Goal｜核心目标

> **How can product information increase the chance of being selected by AI?**  
> 商品信息如何提高被 AI 选中的概率？

The tool is not designed to maximize the amount of product information. It identifies information gaps that affect AI filtering, matching and recommendation, then helps merchants enrich those gaps through guided dialogue.

## 1. Input｜输入

URL first, materials second.

Accepted inputs include:
- Product URL
- Product name
- Keywords
- Price
- Cover/main image
- Detail images
- SKU/specifications
- Parameters
- Description
- Brand/model
- Other existing listing materials

Principle:

> **Bring what you already have.**  
> 直接使用现有上架素材。

Single-product evaluation only｜单次只评估一个具体产品 / SKU。

## 2. Extract｜信息提取

Extract existing product information before asking questions:
- Product facts
- Core specifications
- Functions
- Materials / ingredients
- Use scenarios
- Target users
- Selling points
- Brand information
- Claims
- Evidence / sources attached to claims

Do not evaluate or guess during extraction.

## 3. Identify｜商品识别

Confirm:
- What the product is
- Product category
- Target SKU
- Which information clearly belongs to this product

Category identification must be evidence-based.

## 4. Conflict Check｜信息冲突检查

Check for:
- Title/detail conflicts
- Parameter contradictions
- Mixed versions or SKUs
- Claim/evidence mismatch
- Test data or standards without clear attribution

> **Conflicting information should be resolved before missing information is added.**  
> 先处理冲突，再处理缺失。

## 5. Five-Dimension Evaluation｜五维准备度判断

Evaluate:
1. Accessibility｜信息可达性
2. Information Quality｜信息质量
3. Legibility｜信息可理解性
4. Matchability｜需求可匹配性
5. Confidence｜决策信心

Use readiness levels rather than numeric scores.

## 6. Dynamic Decision Context｜动态决策语境

Do not rely on a fixed category checklist.

Ask:

> For this specific category, which product characteristics commonly affect filtering and recommendation?

Examples:
- Food: allergens, storage, ingredients
- Running shoes: foot shape, running scenario, cushioning, weight
- Sunscreen: skin type, SPF, ingredients, water resistance
- Furniture: dimensions, materials, body/space fit
- Storage devices: capacity, interface, speed, durability, compatibility

## 7. Selection-relevant Gap Detection｜选择相关缺口识别

For each potential gap, judge two paths.

### Path A: Factor Type｜信息重要性类型

**Core Decision Factor｜核心决策因素**  
Commonly directly affects whether the product should enter the candidate set.

**Context-dependent Factor｜情境相关因素**  
Importance depends on the consumer need or scenario.

**Low-relevance Factor｜低相关因素**  
Usually has weak impact on initial AI filtering/recommendation.

### Path B: Verification Status｜验证状态

Verification status is discovered through dialogue, not assumed upfront.

Possible outcomes:
- Verified｜已验证
- Source Available｜有可靠来源可补
- Unknown｜当前未知
- Unverifiable｜暂时不可验证

> **Factor Type decides whether the gap is worth pursuing. Verification Status decides how to pursue it.**  
> 信息类型决定值不值得追，验证状态决定怎么追。

## 8. Action Logic｜动作逻辑

### Core Decision Factor + Verified
Use directly. Do not ask again.

### Core Decision Factor + Missing
Ask whether the merchant has a reliable source such as:
- Brand material
- Supplier material
- Manual
- Test report
- Official documentation

If yes: add after evidence is provided.  
If no: mark Unknown. Do not guess.

### Context-dependent Factor + Verified
Retain for scenario-specific matching.

### Context-dependent Factor + Unknown
Do not automatically chase it. Ask only when it affects a common or likely matching scenario.

### Low-relevance Factor
Do not actively pursue by default.

### Subjective / Unverifiable Information
It may remain as marketing language, but should not be treated as a hard fact or strong recommendation evidence.

## 9. Conversational Enrichment｜对话式信息补全

Rules:
1. Ask one main question at a time.
2. Before asking, verify whether the answer already exists in the provided materials.
3. Prioritize the gap most likely to affect AI selection.
4. Never encourage fabrication in order to increase completeness.
5. A merchant’s subjective answer is not automatically Verified.
6. Upgrade information only when a reliable source supports it.
7. Do not broaden a claim beyond what the evidence explicitly supports.
8. If several consecutive questions on **Core Decision Factors｜核心决策因素** return Unknown / Unverifiable, stop mechanical questioning and evaluate whether a Readiness Warning should be triggered.

> **Evidence should support the exact claim, not a broader interpretation.**  
> 证据只支持它明确覆盖的结论，不扩大解释。

> **Do not optimize completeness at the expense of truthfulness.**  
> 不要为了完整度牺牲真实性。

## 10. Readiness Warning｜信息准备度提醒

Trigger a warning when important selection-related uncertainty remains after conversational enrichment.

Typical trigger conditions include:
- Multiple **Core Decision Factors｜核心决策因素** remain Unknown or Unverifiable.
- Key performance, fit, safety, compatibility, usage-boundary, or risk information cannot be confirmed.
- The merchant repeatedly cannot provide reliable sources for important claims.
- Continuing the optimization would require speculation rather than evidence.

### Trigger Calibration｜触发边界

Do **not** trigger a warning after a single missing answer.

A warning becomes appropriate when uncertainty forms a cluster around the product's core suitability or reliability. In practice, this often means several related Core Decision Factors remain Unknown / Unverifiable and the merchant cannot provide a reliable source.

Validated example — storage device:
- Drive brand: Unknown
- Drive model: Unknown
- Drive new / used status: Unknown
- Verifiable health / test report: unavailable

At this point, further copy optimization does not solve the underlying information problem. The workflow should stop repetitive questioning and warn that source-level information is insufficient.

### Standard Warning｜标准提醒

> **当前仍有多项影响 AI 选择与推荐的关键信息无法确认。**  
> 这可能导致 AI 降低推荐信心，或在部分消费者需求下不将商品纳入候选。  
> 建议优先补充可验证的产品参数、测试资料或供应商信息，而不是自行推测填写。

### High-Uncertainty Warning｜高不确定性提醒

Use a stronger warning when uncertainty affects several core factors or the product’s fundamental reliability / suitability.

> **当前商品存在较高的信息不确定性。**  
> 即使页面信息较完整，AI 仍可能因为关键事实无法验证而降低推荐信心。  
> 建议先补充核心来源信息，再继续优化商品词条。

After a High-Uncertainty Warning:
- Stop asking repetitive questions that are unlikely to produce new evidence.
- Keep unresolved items explicitly marked as Unknown / Unverifiable.
- Allow the workflow to continue with known information only.
- Keep **Confidence｜决策信心** appropriately low if the unresolved factors materially affect recommendation.
- Recommend source-level next actions such as supplier documents, SMART / diagnostic results, test reports, manuals, or official specifications where relevant.

Principles:
- Do not trigger warnings merely because any field is missing.
- Warnings should depend on **selection relevance**, not raw missing-field count.
- Unknown information should remain Unknown. Do not pressure the merchant to invent an answer.
- A warning is a diagnostic outcome, not a failure state.

## 11. Re-evaluate｜重新评估

After enrichment and any readiness warning, re-evaluate the same five dimensions and compare before vs after.

Do not use numeric scores. Use **Readiness Level｜准备度** with qualitative status and, where useful, progress bars.

## 12. Confirmation｜用户确认

After the before/after comparison, stop and ask:

> 以上变化是否与你掌握的商品信息一致？如果有不准确的地方，请指出，我会先修正。

Do not generate the final enriched listing before confirmation.

## 13. Final Output｜最终完整词条

After confirmation, output the complete enriched product listing, including:
- Original verified information
- Newly added verified information
- Scenario-specific matching information
- Clear limitations
- Relevant Unknown / Unverified items
- Any active Readiness Warning if key uncertainty remains

Do not output only the changes.

## 14. Response Style｜Skill 回答风格

**Short, guided, conversational｜简短、引导式、对话化**

- Chinese-first, with English labels when useful
- Short sentences
- Natural paragraph breaks
- Conclusion before explanation
- One main issue/question at a time
- Avoid long technical walls of text
- Avoid asking the merchant to complete a large form

## Workflow Summary

Input  
→ Extract  
→ Identify  
→ Conflict Check  
→ Five-Dimension Evaluation  
→ Dynamic Decision Context  
→ Selection-relevant Gap Detection  
→ Factor Type × Verification Status  
→ Conversational Enrichment  
→ **Readiness Warning**  
→ Re-evaluate  
→ Before/After Comparison  
→ User Confirmation  
→ Final Enriched Listing
