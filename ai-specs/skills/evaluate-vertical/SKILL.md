---
name: evaluate-vertical
description: Use when the question is "should we enter vertical X?" or "what would X need to run on our platform?". Produces an enter/don't-enter decision with an explicit criterion and a breakdown of what gets reused from the platform vs. what's specific to the vertical.
---

# Evaluate a new vertical

Goal: decide whether the company should enter a vertical, and if so, what gets built once as a configurable capability vs. what's specific. This is the central exercise of this function.

## When to use it

- You're asked "should we enter vertical X?".
- You need to know what a new vertical would require to run on the existing platform.
- You need to decide what gets built once as a configurable capability vs. what's specific to the vertical.

## Starting questions (ask these before producing anything)

1. Who operates this vertical and what's their daily workflow?
2. What's the core workflow or system this vertical needs to plug into, and what integration does that require (API, a specific compliance/certification, a data format, an existing tool, other)?
3. What blocks entry today, a product gap or a commercial issue?
4. What's the vertical's size and purchase frequency? (defines whether the current business model can sustain it)

## Step 1 — Vertical profile

Fill in:

```
Vertical: [name]
Typical user: [who directly uses it day to day]
Typical buyer: [who pays, if different from the user]
Estimated average ticket: [currency amount] · Frequency: [high/medium/low]
Required integration: [API / a specific compliance-certification / a data format / an existing tool / unknown]
Why now: [what makes it relevant]
```

## Step 2 — The platform vs. specific matrix (the heart of the analysis)

For each need of the vertical, classify it:

| Vertical need | Already exists on the platform? | Configurable or specific build? | Justification |
|---|---|---|---|
| User authentication (SSO) | Yes | Configurable | Already core |
| [e.g.: time/usage-based session] | Partial | Configurable | Already exists in another vertical |
| [e.g.: access control] | No | Evaluate build | New format |
| [e.g.: advance booking] | No | Evaluate build | New format |

Rule: if something resembles a capability that already exists for another vertical, it's configurable, not a new build. A specific build is only justified when the need has no analog on the platform.

## Step 2b — Build or integrate?

For each need that comes out as a specific build, ask before assuming it gets built: does something already exist on the market that we could integrate to enter fast? Integrate to validate entry; build only what's differentiating and core. If this becomes the axis of the decision, chain into `business-case`.

## Step 3 — Decision

```
Recommendation: [ENTER / DON'T ENTER / ENTER IN PHASE 2]
Decision criterion: [revenue / speed / maintenance risk]
What would get built first: [the minimum capability]
What's out of this phase: [explicit]
Biggest risk: [the one that would kill entry]
Open question for Commercial / the platform PM: [one]
```

## Expected output

A filled platform-vs-specific table + three sentences of recommendation. No more.

## How it connects with the rest

If step 2b's build-vs-integrate becomes the axis of the decision, follow with `business-case`. To specify the capability that would get built first, follow with `write-spec`.

## Not complete if...

- Not complete if any row of the platform-vs-specific matrix has no justification.
- Not complete if the recommendation isn't ENTER / DON'T ENTER / ENTER IN PHASE 2 with an explicit criterion.
- Not complete if a specific build didn't go through the build-vs-integrate question (step 2b).
