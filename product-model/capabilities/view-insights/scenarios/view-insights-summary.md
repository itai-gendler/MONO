---
kind: primary
routes:
  main: Main path
steps:
- text: The User requests the local summary.
  kind: actor
  entities: []
  actor: user
  contexts:
    main:
      place: web::insights
- text: The Product derives the summary from Items.
  kind: product
  entities:
  - entity: item
    effect: reads
    facts:
    - Priority
    - Tags
    - Completed at
  actor: user
  contexts:
    main:
      place: web::insights
references:
- kind: code
  role: implementation
  target: src/components/intelligence/InsightsDashboardModal.tsx#InsightsDashboardModal
- kind: code
  role: implementation
  target: src/lib/intelligence/productivityInsights.ts#calculateProductivityInsights
---

# Review productivity

## Trigger

The User opens Insights.

## Outcome

The summary shows completed against total items, the completion percentage, items completed in the last seven days, the count per priority, the most used tag, and recommendations.

## Edge cases

- No items yields zero completion rate and no top tag.
