# Company context (feeds the copilot)

STABLE context the AI copilot preloads before working on any spec. Fill this in once per
project, before running `/discovery` for the first time.

Context is split by data nature into three documents: this one (stable, preloaded),
`docs/doc_market_research.md` (live, dated, changes fast, refreshed by the `live-research`
skill), and `docs/doc_open_questions.md` (what we don't know, asked of the team, never
invented).

## What the company is

[FILL IN: who they are, what they do, in one or two sentences. If this isn't a
traditional company (a personal project, a side project, a portfolio), say so explicitly,
same as here.]

## Core product(s)

[FILL IN: what it builds or sells, for whom. If there are several products/lines, list
them with one sentence each.]

## Business model

[FILL IN: how it makes money today — or, if it doesn't apply (a project with no
monetization), say so and reframe what the real "output" that matters is.]

## How the business works (inferred vs. confirmed)

[FILL IN: real facts about the business, each one tagged `[CONFIRMED]` or
`[ASSUMPTION — verify]`. Don't mix the two without marking which is which — that's this
harness's hard rule, see `docs/doc_base_standards.md`.]

## Current verticals / segments

[FILL IN: who it sells to or serves today, as precisely as possible — geography, client
size, user type.]

## Business goals

[FILL IN: what it's trying to achieve, in real priority order (primary/secondary/
tertiary), and any hard constraint product decisions can't violate.]
