---
name: validate-fast
description: Use to define the cheapest test that confirms or kills a hypothesis before committing engineering. Keeps the PM from being the bottleneck by asking for builds to validate things that can be validated without code.
---

# Validate fast, before escalating

Goal: don't ask engineering to build something to find out if the idea works. Define the cheapest validation first.

## When to use it

- There's a product hypothesis and you need the cheapest test that confirms or kills it.
- Someone's about to ask engineering for a build for something that could be validated without code.
- Time to fill in a spec's "how it's validated" section.

## Step 1 — State the hypothesis as something falsifiable

```
We believe [user] will [behavior] because [reason].
We'll know it's true if [metric] clears [threshold] within [timeframe].
We'll kill it if [failure signal].
```

## Step 2 — Choose the cheapest method that answers it

Order from cheapest to most expensive; use the first one that genuinely answers it:

1. **Data that already exists** — does the backoffice/analytics already have data from another context that answers this without building anything?
2. **Smoke test / fake door** — a button or screen that measures intent with no real backend behind it.
3. **Concierge / manual** — do the flow by hand before automating it.
4. **AI-built prototype** — an artifact that shows the flow for a user test (links to `build-prototype`).
5. **Real MVP** — only if the four above aren't enough.

## Step 3 — Design the concrete test

```
Method chosen: [one of the 5]
With whom: [real operating partner / end user / sales team]
What it measures exactly: [the metric]
Success threshold: [number]
Timeframe: [days]
Cost (time/money): [estimate]
```

## Golden rule

If the validation requires more engineering effort than building the whole feature, you're validating wrong. Step down one rung on the list of methods.

## With small datasets

Present the result as a directional indicator, not as a conclusion. "Signal that X" instead of "X is proven."

## Expected output

The falsifiable hypothesis + the chosen method with its threshold. Three lines. This goes inside the spec, in the "how it's validated" section.

## How it connects with the rest

Receives from `write-spec` (the "how it's validated" section, written in its first pass) and from `build-prototype` (reordered 2026-09-17: now runs right after the low-fidelity prototype, so it validates against the real flow that already exists, not just a hypothesis on paper). If the chosen method involves talking to real people (interview, concierge, smoke test with follow-up), follow with `human-validation` for the execution script.

## Not complete if...

- Not complete if the hypothesis isn't falsifiable, meaning it doesn't say what would kill it.
- Not complete if a method was chosen without first ruling out the cheaper ones on the list.
- Not complete if the numeric success threshold is missing.
