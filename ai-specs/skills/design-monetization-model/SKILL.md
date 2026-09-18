---
name: design-monetization-model
description: Use when the question is how to monetize a shared touchpoint (a screen, a space, an interaction) without breaking the experience of whoever uses it. Produces a monetization model chosen from several candidates, with the trade-off reasoned out, not a blind rule.
---

# Design the monetization model for a touchpoint

Goal: given a touchpoint shared between several parties, choose the monetization approach that best balances three things in tension. There's no fixed correct answer; the work is reasoning through the trade-off for THIS touchpoint and this context. That's exactly what makes the problem hard: picking the best model for the business without adding friction.

## When to use it

- You're asked how to monetize a specific touchpoint (a screen, a space, a moment in someone's experience).
- Entry into a vertical or touchpoint has already been decided and it's time to pick the revenue model.
- Someone proposes "let's put ads here" and it needs comparing against the other options before accepting it.

## The problem has three sides, always

Every monetization model for a shared touchpoint has to resolve all of these at once:

1. **The touchpoint owner**: why would they say yes? Fee discount, commission on a sale, a new service that gives them value, data about their users. Without their yes, nothing runs.
2. **The paying third party**: what are they buying and why is it worth their money? Reach, context, intent in the moment.
3. **The end user**: their experience. An almost-automatic process breaks easily. This is where the friction lives.

## Step 1 — Map the possible models (don't marry ads)

Advertising is one option, not the only one. For the given touchpoint, list which ones apply:

| Model | What it is | Who pays | Moment |
|---|---|---|---|
| Ad / sponsored placement | An ad or sponsored result at the touchpoint | Third party | Before / during / after the interaction |
| Marketplace / referral commission | Company takes a % of a transaction it helped facilitate | Third party | At the transaction |
| Revenue share to the touchpoint owner | The owner gives up a cut or a fee reduction in exchange for hosting the monetized surface | (Offset by third-party revenue) | Contract |
| Freemium upsell / pre-commit | Paying to unlock or reserve something used later | End user | During a natural pause in the flow |
| Paywall / gated access | The touchpoint is the gate to content, a feature, or an event | End user / organizer | On access |
| Pay-per-use / metered feature | A paid action or session at the touchpoint | End user | At the touchpoint |

## Step 2 — The axis that decides everything: friction vs. moment

Place each candidate model by WHEN it touches the end user:

- **Before the interaction**: maximum friction. Interrupts someone who came to do something else. Almost always bad unless the context has real long waiting time.
- **During the interaction**: breaks an almost-automatic process. Dangerous.
- **After the interaction**: the challenge is retaining someone who's already leaving. Needs a strong hook (a discount code, a saved draft, a useful follow-up) and seconds, not minutes.
- **During an idle moment**: the golden window — any real waiting or empty moment in the flow (a loading screen, an empty state, between two steps). This is where upsells, pre-commits, and add-on offers fit.

## Step 3 — Context rules

The same model wins or loses depending on where and when the touchpoint happens. Reason it out explicitly:

```
Context: [describe the real environment: rushed, waiting, mid-task, just browsing...]
User state: [rushed / waiting / mid-task, focused / just browsing]
What this context allows: [which models make sense here]
What it does NOT allow: [what would break the experience here]
```

Example reasoning (generic, adapt to the real context): if the user is mid-task and rushed, an ad before they can proceed is pure friction; but a pre-commit offer they can redeem later uses the urgency in your favor. If the user hits a genuine idle moment (a loading state, an empty results page), offering something useful there is high value and zero friction to the task itself.

## Step 4 — Choose and reason the trade-off (no fixed hierarchy)

No single axis always wins. Weigh all three and state your decision:

```
Model chosen: [one]
What the touchpoint owner gains: [their incentive to accept]
What the paying third party gains: [why they pay]
Friction for the end user: [where it touches them and why it's acceptable HERE]
Why this one and not the other two candidates: [the explicit trade-off]
What would kill it: [the condition that makes it unviable]
```

The criterion in one sentence: you don't pick the model that earns the most, or the one that bothers the least, in the abstract; you pick the one that best balances all three for this touchpoint and this context, making explicit what gets sacrificed.

## Platform vs. specific note

The context gets modeled as a configurable variable (touchpoint type, user state, time window), not as a per-site build. A good monetization model is a capability that gets parameterized by context. That keeps it faithful to the principle of not creating an unmaintainable mosaic.

## Two-sided validation

A touchpoint model doesn't get validated with a single metric. You need signal from both sides: does the touchpoint owner accept the deal? Does the third party pay? Does the end user not abandon? The cheapest test is usually testing the more fragile side first (usually the touchpoint owner's acceptance or the end user's friction), not whichever is easiest to measure.

## Expected output

The map of possible models (step 1) + the reasoned decision (step 4): model chosen, what each of the three sides gains, and what would kill it.

## How it connects with the rest

Follow with `write-spec` for the chosen capability, and with `validate-fast` to design the two-sided test above.

## Not complete if...

- Not complete if the three sides (touchpoint owner, paying third party, end user) weren't named and what each one gains.
- Not complete if it doesn't say at what moment (before / during / after the interaction / an idle moment) the chosen model touches the user.
- Not complete if "advertising" was the only model considered.
- Not complete if it doesn't say what would kill it.
