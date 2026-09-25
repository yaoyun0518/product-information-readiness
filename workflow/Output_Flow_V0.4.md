# Output Flow V0.4

## Step 1｜五维前后对比

Use a comparison table with these columns:

| 维度 | 优化前 | 优化后 | 变化 |
|---|---|---|---|
| 信息可达性 |  |  |  |
| 信息质量 |  |  |  |
| 信息可理解性 |  |  |  |
| 需求可匹配性 |  |  |  |
| 决策信心 |  |  |  |

Rules:
- Use readiness levels rather than numeric scores.
- Progress bars may be used as a visual aid.
- In the **变化** column, separate each change into its own line or paragraph.
- Do not compress several changes into one long sentence.

## Step 2｜Merchant Context Test｜商户消费者语境测试

Before the final listing, ask the merchant for 2–3 real high-frequency consumer contexts.

For each context, collect only:
- Who the consumer is
- Why they buy
- What matters most
- Hard constraints
- Secondary / nice-to-have factors

Use the enriched product information to test whether AI can make a context-appropriate selection judgment.

The goal is not to maximize recommendation rate. The goal is to test whether the current information supports the right recommendation boundary for different consumers.

## Step 3｜Context Gap Check｜语境缺口检查

After the context test, check whether important gaps remain.

Examples:
- A feature exists but reliability is still unknown
- A usage boundary is missing
- Safety, fit, compatibility, or evidence is insufficient in an important consumer context
- The same Unknown becomes critical in one context but secondary in another

If no important gaps remain, proceed to confirmation.

If important gaps remain, explain them concisely and ask:

> 在你提供的消费者场景中，仍有几项信息会影响 AI 的选择判断。是否继续进行下一轮信息补充？

### If merchant chooses Yes

Return to conversational enrichment and only ask about the newly surfaced selection-relevant gaps.

Then repeat:

**Enrich → Re-evaluate → Merchant Context Test → Context Gap Check**

### If merchant chooses No

Stop iteration and preserve the first-round confirmed enrichment result.

Unresolved information must remain clearly marked as Unknown / Unverified. Keep any relevant Readiness Warning.

## Step 4｜用户确认

After the final chosen iteration, stop and ask:

> 以上变化是否与你掌握的商品信息一致？如果有不准确的地方，请指出，我会先修正。

Do not generate the final listing before confirmation.

## Step 5｜Final Enriched Listing｜变化后的完整商品词条

Only after the user confirms, output the complete revised listing.

It should include:
- Original verified information
- Newly added verified information
- Scenario-specific matching information
- Clear limitations
- Relevant Unknown / Unverified items
- Any active Readiness Warning

The final output is a complete product information set, not a change log.

## Step 6｜After Publishing｜上架后复评

Close the final output with this fixed reminder:

> 商品上架后，可再次提交详情页进行复评，检查实际页面是否仍存在影响 AI 选择与推荐的信息缺口。

Purpose:
- Extend the workflow from pre-publishing optimization to post-publishing review.
- Re-evaluate the actual live product page rather than relying only on pre-publishing materials.
- Check whether information was lost, changed, mixed across SKUs, or presented unclearly after publishing.

This step is a fixed closing message and should remain concise.
