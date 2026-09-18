---
name: prioritize-roadmap
description: Use when there are several options on the table (several verticals, several monetization formats, several features) and you need to decide the order. Produces a prioritization with an explicit criterion and a one-line recommendation, not an open debate.
---

# Prioritize the expansion roadmap

Goal: order options with a communicated criterion, not with intuition. The criterion matters as much as the result.

## When to use it

- There are several verticals, formats, or features on the table and you need to decide the order.
- Someone asks to "prioritize this" without giving a criterion, and one needs to be stated before scoring.
- A closed recommendation is needed, not an open debate.

## Step 0 — Fix the criterion before scoring

Ask or state: are we prioritizing by revenue impact, by delivery speed, or by reducing platform-maintenance risk? Write it above everything else. Changing the criterion changes the order, so it gets decided first.

## Step 1 — RICE (or whichever framework applies)

| Option | Reach | Impact (1-3) | Confidence (%) | Effort (person-weeks) | Score |
|---|---|---|---|---|---|
| A | | | | | |
| B | | | | | |
| C | | | | | |

Score = (Reach × Impact × Confidence) / Effort.

Say the assumption behind each cell out loud. With little information, mark Confidence low instead of inventing Reach.

## Variant: if the criterion is maintenance risk

When the dominant criterion is not breaking the platform, replace Impact with "platform reuse":

| Option | % reuses the platform | Specific builds required | Maintenance debt | Priority |
|---|---|---|---|---|

Whatever reuses the most and requires the fewest one-off builds rises, even if its commercial impact isn't the biggest. This respects the principle of not creating an unmaintainable mosaic of builds.

## Step 2 — Recommendation

```
First: [option] because [criterion].
Second: [option].
Not now: [option] because [reason, usually disproportionate risk or effort].
Assumption that would move this order the most if it changed: [one].
```

## Expected output

Table + three lines of closed recommendation. Never leave the decision open "to discuss"; give your recommendation and say what would change it.

## How it connects with the rest

Receives from `business-case` or `evaluate-vertical` when several options have already been evaluated separately. Follow with `write-spec` for the option that comes out first.

## Not complete if...

- Not complete if the criterion wasn't stated before scoring.
- Not complete if any Confidence cell is invented instead of marked low for lack of information.
- Not complete if the recommendation is left open "to discuss" instead of closed.
