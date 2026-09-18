# Base standards

Principles that govern any work in this repo. The copilot always respects them.

## How decisions get made

- **Explicit criterion, always.** No prioritization without saying what it's based on (revenue impact, delivery speed, maintenance risk). The criterion gets communicated, not just the result.
- **Assumptions out loud.** When information is missing, assume the minimum needed to move forward and mark it as [ASSUMPTION — validate]. Don't ask for more info than necessary.
- **Platform vs. specific.** Every vertical feature goes through the question: does this get built once as a configurable capability, or is it genuinely specific to this vertical? The answer gets justified.
- **Findings as indicators.** With small data, findings get presented as directional signals, not as definitive conclusions.

## How things get specified

- **The spec is the durable artifact, the prompt is disposable.** Anything that's actually going to get built goes through a spec.
- **Acceptance criteria in EARS format.** Patterns: `WHEN [event] THE SYSTEM SHALL [behavior]`, `IF [condition] THEN [behavior]`, `WHILE [state] THE SYSTEM SHALL [behavior]`. No adjectives ("fast", "intuitive") as a criterion; only measurable behavior.
- **Explicit out of scope.** Every spec states what does NOT get built in this version.
- **Minimum viable spec.** Write just enough to remove ambiguity for the next phase, not a thirty-page PRD before validating anything.

## How things get validated

- **The cheapest test first.** Before committing engineering, define the fastest validation that confirms or kills the hypothesis.
- **The PM validates before handing off.** Where possible, prototype with AI so engineering doesn't waste time on something with an obvious UX or scope problem.
- **One number per hypothesis.** Every spec says which metric would confirm it worked.

## How the harness itself changes

Applies to any edit to `CLAUDE.md`, `README.md`, `ai-specs/skills/*/SKILL.md`, `ai-specs/.commands/*.md`, or `docs/`, regardless of which copilot or session makes it.

- **Verify integration before touching anything.** Before editing a skill, a command, or a doc, search (grep) every place the concept you're about to change is already mentioned — `CLAUDE.md`'s routing table, `README.md`'s diagram, other `SKILL.md` files. A change that breaks a reference in another file isn't done, it's half-done.
- **Every new skill/command gets declared in three places, not one.** The file itself (`ai-specs/skills/<name>/SKILL.md` + `ai-specs/.commands/<name>.md`), `CLAUDE.md`'s routing table, and `README.md`'s structure diagram. Miss any of the three and the skill exists but is invisible to the next session.
- **Test before and after, not just after.** Before changing: check what's true today (count how many skills/docs really exist, what cross-references exist). After: repeat the same check and verify it matches — no count ("four docs", "eleven skills") can drift out of sync with the repo's reality.
- **Nothing gets assumed, it gets checked.** If the question is about an external practice (what's the standard order for X?), that's `live-research`, not a reasoned guess — same as with any other market data point.
- **Definition of "done" for a change to the harness:** a copilot in a new session, with no memory of this one, has to be able to follow the complete trail from `CLAUDE.md` to the final file without a single broken link.

## Writing tone

Simple, direct, human. No buzzwords, no language that sounds like AI. No em dashes. When there are three factors, say "three," not "several."
