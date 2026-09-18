---
name: human-validation
description: Use once validate-fast has chosen the method (smoke test, concierge, interview). This skill is the HOW of executing it well: script, sample size, and how to keep people's politeness from disguising itself as validation. Especially important in two- or three-sided models (touchpoint owner, paying third party, end user).
---

# Execute validation with humans

Goal: make the validation measure real behavior, not polite opinions. The most common mistake isn't picking the wrong method, it's executing it in a way that makes everyone tell you yes.

## When to use it

- `validate-fast` already chose the method (smoke test, concierge, interview) and it's time to execute it well.
- The model has two or three sides (touchpoint owner, paying third party, end user) and each needs validating separately.
- There's a risk that people's politeness will disguise itself as validation.

## Golden rule: ask for commitment, not opinion

"Would you like this?" almost always gets a false yes, people are nice. Ask something that costs them a little:

| Instead of asking | Ask / observe this |
|---|---|
| "Would you pay for this?" | "Here's the payment link, complete it if you're interested" |
| "Would an ad here bother you?" | Show it to them for real and measure whether they leave |
| "Would you use the pre-order?" | Offer it once and measure whether they complete it, not whether they say yes |
| "Would you accept this deal?" | Put the concrete figure on the table (a discount of X€ or a commission of Y%) and measure whether they sign or ask to think it over |

The real signal is in the friction the person is willing to cross, not the word they say.

## How many people you need (and why you don't need more)

For an early directional signal, not for a launch:

- **Usability / friction of a flow**: 5 people catch most of the obvious problems. After the fifth, you start seeing the same problems repeat.
- **Desire or purchase intent**: 10 to 15 conversations give a reasonably directional read. Fewer than that, any pattern could be noise.
- **Operating-partner acceptance (B2B, expensive decision)**: 3 to 5 real conversations are enough if they're with the right profile, because each B2B conversation weighs far more than one consumer survey response.

With samples this small, the result always gets reported as a directional indicator, never as a conclusion.

## The script, for each side of the model

**With the end user**
1. Let them use the flow without helping. Don't explain what you expect them to do.
2. When they get stuck, don't rescue them right away, note where and for how long.
3. At the end, ask "tell me what went through your head at moment X" (retrospective on a specific moment), not "what did you think?" (general opinion).
4. Never ask if something "is a good idea." Ask if they'd do it again, or if they'd recommend it to someone specific.

**With the touchpoint owner / operating partner**
1. Don't sell them the idea in the same conversation where you validate it, it contaminates the signal.
2. Put the real figure on the table (a fee discount of X€, or a commission of Y%), not "we'd be thinking about something like this."
3. Measure the reaction to the figure, not to the idea in the abstract. If they hesitate once the figure is on the table, that hesitation is the data.
4. Close by asking for a concrete next step (a real pilot, a letter of intent), not "what do you think?"

**With the third party who'd pay**
1. Talk to someone who already buys something comparable today, not just any generic contact.
2. Ask what they pay today for something equivalent, to get a real price anchor.
3. The strong signal is them asking for a formal proposal or a paid pilot, not saying "interesting."

## False signals to rule out

- Everyone says yes in the interview, but nobody completed the requested commitment: the idea is liked in the abstract, not in practice. Weak signal.
- You only validated with people who already like you or know you: friendliness bias. Repeat with strangers before trusting the result.
- You asked about the future ("would you use it?") instead of the past or present ("did you use it just now?", "tell me about the last time something like this happened to you"): people are bad at predicting their own future behavior.

## How to communicate it

The short way to explain how this gets executed, without just listing methods: "I don't ask if they like it, I ask them to do something that costs them a little, and if they do it, that's the signal. With data this small from a first round, I treat it as an indicator, not a conclusion."

## Expected output

```
Method executed: [from validate-fast]
With whom and how many: [profile + number]
Commitment asked for (not opinion): [what cost the person something]
What was observed: [real behavior, not what they said they felt]
Signal: [STRONG / MIXED / WEAK] — never "confirmed" with a small sample
What would kill it if it repeated: [the negative pattern that would invalidate the idea]
```

## How it connects with the rest

Receives from `validate-fast` once the method is chosen. The result (STRONG / MIXED / WEAK signal) feeds the decision already framed in `business-case` or `design-monetization-model`.

## Not complete if...

- Not complete if any question in the script asks for opinion instead of commitment.
- Not complete if the sample doesn't reach that category's minimum (5 for usability, 10-15 for purchase intent, 3-5 for B2B acceptance).
- Not complete if the signal is reported as "confirmed" with a small sample.
