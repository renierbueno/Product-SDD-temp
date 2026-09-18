---
name: business-case
description: Use to make the case for a product decision in business terms and defend it to Commercial or the Product Director. Doesn't assume any fixed revenue model. Produces the case for a decision, with the trade-off and the biggest risk made explicit.
---

# Make the business case

Goal: turn a product decision into a business argument someone from Commercial or Leadership can understand and push back on, and detect which gaps block entry into a new vertical or model, not just defend a decision already made.

Important: if the company is opening up new business models, do NOT assume everything has to fit the current model (`docs/doc_company_context.md`). The point is the opposite: finding the best model for each case. The current model is the base, not a restriction on what's new.

## When to use it

- A product decision has already been made and needs to be defended to Commercial or Leadership.
- Build vs. integrate needs deciding and justifying in business terms.
- Someone asks "how much could this move revenue?" and the answer needs explicit assumptions, not a number pulled from nowhere.

## The case, in five pieces

```
Decision: [what gets built or entered]

Why the business needs it:
[the problem or opportunity in terms of money or position, not features]

How it makes money (or how it's sustained):
[the model: subscription, usage-based pricing, commission/take-rate, advertising, mix.
 Say which one and why it fits better than the alternatives. There's NO default answer here.]

What it costs and what it risks:
[build effort + the real risk, including platform-maintenance risk]

Why now:
[what makes it urgent; what happens if we wait]
```

## The questions Commercial will ask you (anticipate them)

- How much could this move revenue, and over what timeframe? (even a range with assumptions)
- Which clients/accounts does this unlock?
- Will the client/partner want this, or do we have to push it on them?
- What happens to margin if the model carries new variable cost?
- Does this tie us to an external provider? (build vs. integrate)

Have an answer, even with marked assumptions, for each one.

## Build vs. integrate (a business decision, not just a technical one)

When the case involves a new capability (a billing engine, a reporting dashboard, a notifications system, an integrations marketplace), the question that really decides it is: **does this touch the company's exclusive asset (its network, its customer relationship, its own data), or is it generic infrastructure a third party already solves better?**

```
Does it touch the company's exclusive asset?: [yes / no]
What already exists that we could integrate? [name the real market options]
Cost of integrating: [fast but dependency + margin ceded to a third party]
Cost of building: [slow but it's a proprietary, differentiated product]
Recommendation: [one] because [criterion: speed to market / differentiation / margin / data control]
```

The honest rule: if it touches the exclusive asset, build it; if it's generic, integrate to enter fast and validate, and only evaluate building if volume justifies it. State which is which in this case.

## With small data or assumptions

Present the numbers as scenarios with visible assumptions, not as firm projections. "If we assume X accounts and a Y ticket size, this lands around Z" is honest; a lone figure looks invented. Frame findings as directional indicators.

## Expected output

The five pieces of the case + the build-vs-integrate decision if applicable. Short and defensible. The test of a good case: someone from Commercial could push back on it with data, not with "I'm not convinced."

## How it connects with the rest

Receives from `evaluate-vertical` (step 2b) or `design-monetization-model` when build-vs-integrate is the axis of the decision. Follow with `prioritize-roadmap` if there are more options on the table, or straight to `write-spec` if it's already decided.

## Not complete if...

- Not complete if any of the five pieces of the case is missing.
- Not complete if the numbers don't carry visible assumptions.
- Not complete if it involves a new capability and build vs. integrate wasn't answered.
