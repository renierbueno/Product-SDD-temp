---
name: live-research
description: Use when a data point is missing during a session and needs to be looked up in the moment. Covers five types of market data (vertical size, monetization comparables, regulation, price benchmarks, user behavior), not just competitors. It's for LIVE context that doesn't live in docs. Produces structured findings the rest of the harness can consume, always marked as a directional signal.
---

# Live research

Goal: bring in data we don't have preloaded, in the moment, without breaking the rest of the flow. The harness's principle is that stable context lives in `docs/` and live context gets looked up. This skill is the "looked up," and it covers more than competitors.

## When to use it

Use it for any of the five categories below. Do NOT use it for internal company/project data (own metrics, real ICP, churn): that doesn't get looked up, it gets ASKED of the team, and goes to `doc_open_questions.md`. Also do NOT use it to reread something already in `docs/doc_company_context.md` or `docs/doc_market_research.md`; check first whether you already have it.

## The five categories, and which decision each one feeds

**1. Size and growth of the specific vertical**
The size of the general category isn't the same as the size of the specific vertical being asked about (how many players there are, whether the sector is growing or stagnant, how fragmented it is between many small operators or a few large chains).
Sample question: "market size [vertical] [country] [year]", "number of operators [sector] fragmentation [region]".
Feeds: `evaluate-vertical` (the enter-or-not decision) and `prioritize-roadmap` (a RICE's Reach).

**2. Monetization comparables**
Who's already doing something similar and how they charge for it.
Sample question: "who monetizes something similar to [touchpoint] in [context]", "revenue model [comparable]".
Feeds: `design-monetization-model` (which models exist) and `business-case` (precedent to defend the decision).

**3. Regulation specific to the vertical or the model**
The category people skip most often, and the one that most quickly gives away someone who hasn't fully thought through the problem. Any model that segments by behavior or location touches data protection. Certain product or service categories have their own restrictions.
Sample question: "location-based targeted advertising data protection regulation", "[vertical] regulation [country]".
Feeds: `evaluate-vertical` (Step 2b, build vs. integrate) and `business-case` (what's at risk).

**4. Unit price benchmarks**
Without this, any revenue projection in `business-case` is a made-up number. You need the anchor: how much a comparable CPM is worth, what a typical commission in the sector is, how much someone pays to acquire a similar contact or conversion.
Sample question: "average CPM [format] [country]", "typical commission [sector]".
Feeds: `business-case` (the revenue scenario with visible assumptions) directly, that block can't be written without this.

**5. User behavior in that type of context**
Industry data on how people react to a format, not your own opinion. QR-code scan rates at a physical point, conversion rates of interactive screens, how much attention span a comparable format captures.
Sample question: "conversion rate [format/channel] benchmark", "attention time [format] benchmark".
Feeds: `design-monetization-model` (the friction-vs-moment axis stops being intuition and becomes an argument).

All of them also feed `human-validation`: an industry benchmark is the threshold you compare your own signal against when you validate with real people.

## How to search without losing the session

1. **One concrete question per search**, within a single one of the five categories. Don't mix "market size and regulation" in one search.
2. **Before searching, decide which decision it changes.** If the data point doesn't move a decision in the session, don't look it up.
3. **Maximum 2 or 3 searches per question.** If nothing turns up, say there's no clear public data and move on with the assumption marked.
4. **Prioritize the original source** (sector report, regulator, the comparable company's own site) over aggregators.
5. **Failure cases count too**, not just successes. Actively look for whether any category-2 comparable failed or shut down.

## Honesty rule (the most important one)

- A comparable isn't validation. It proves someone does it, not that it'll work here.
- A sample of one or two companies per vertical = directional signal, never a conclusion.
- Never invent a figure to fill a gap, whether market or price data. If there's no public data, the output is "no reliable public data, this stays as a question for the team."
- Don't mix external data (this gets looked up) with internal company/project data (this gets asked). If the question is about the company itself, it's not this skill's job, it goes to `doc_open_questions.md`.

## How to communicate it

Say the state of the data out loud at the moment you look it up, don't hide it inside the final answer: "I don't have this preloaded because it changes fast, so I'm looking it up now." And, depending on the category: "I found [X], but it's a single company, so I'm treating it as a direction, not proof" (category 2 or 5), or "without a price benchmark I can't give a responsible revenue figure, so I'm looking it up before proposing a number" (category 4), or "before proposing this model, I'd need to confirm whether there's any regulatory restriction, checking now" (category 3).

## Expected output

```
Category: [1-5, from the list above]
Question it answers: [the decision that was blocked]
Finding: [the data point, in one sentence]
Source and date: [where from, when]
Size of the evidence: [one company / one report / a repeated pattern across several]
Signal strength: [STRONG if several sources agree / WEAK if it's a single case]
What decision it changes: [how it affects the session]
Assumption this would leave in place if true: [what you're assuming from here on, tagged for the team to validate]
```

## How it connects with the rest

- Categories 1 and 3 → `evaluate-vertical`.
- Category 2 → `design-monetization-model` and `business-case`.
- Category 4 → `business-case`, mandatory before giving any revenue figure.
- Category 5 → `design-monetization-model`, and an anchor for `human-validation`.
- An assumption you confirm or knock down gets updated verbally in the session; `docs/doc_market_research.md` does NOT get rewritten on the fly, the doc is stable, dated context, the session is ephemeral.

## Not complete if...

- Not complete if the finding doesn't state the size of the evidence and the signal strength.
- Not complete if it mixes external data with internal company/project data.
- Not complete if the search happened without a concrete decision blocked by that data point.
