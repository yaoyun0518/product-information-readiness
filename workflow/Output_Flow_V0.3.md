# Output Flow V0.3

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

## Step 2｜用户确认

After the table, stop and ask:

> 以上变化是否与你掌握的商品信息一致？如果有不准确的地方，请指出，我会先修正。

Do not generate the final listing before confirmation.

## Step 3｜Final Enriched Listing｜变化后的完整商品词条

Only after the user confirms, output the complete revised listing.

It should include:
- Original verified information
- Newly added verified information
- Scenario-specific matching information
- Clear limitations
- Relevant Unknown / Unverified items

The final output is a complete product information set, not a change log.

## Step 4｜After Publishing｜上架后复评

Close the final output with this fixed reminder:

> 商品上架后，可再次提交详情页进行复评，检查实际页面是否仍存在影响 AI 选择与推荐的信息缺口。

Purpose:
- Extend the workflow from pre-publishing optimization to post-publishing review.
- Re-evaluate the actual live product page rather than relying only on pre-publishing materials.
- Check whether information was lost, changed, mixed across SKUs, or presented unclearly after publishing.

This step is a fixed closing message and should remain concise.
