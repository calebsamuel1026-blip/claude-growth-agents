# claude-growth-agents

Three Claude Code subagents for growth strategy that is backed by evidence, not opinion.

- `growth-advisor`: reads your real numbers and a public content feed you collect, turns ideas from published growth frameworks into concrete "plays", and returns the top 3 moves for the week. It applies frameworks in its own words and never claims to be their author. Money, pricing, legal and account decisions go to the owner.
- `market-intel`: studies comparable businesses and published cold-email results. Records source, date, sample size and vendor bias for every claim, extracts patterns instead of copying text, and turns findings into "copy 1:1", an A/B test spec, or "no change".
- `catalog-builder`: designs a service catalog where every product is tied to a money lever for the customer, mapped to a gap you can detect, and rated on whether you can actually deliver it. Prices stay proposals until the owner approves them.

## Install

```
cp agents/*.md ~/.claude/agents/
# or, for one project
cp agents/*.md <your-project>/.claude/agents/
```

Restart Claude Code or run `/agents` to check they load.

## Files you need to create

Paths are relative to your project. `<project>` is your project folder. Edit the agent files if your layout differs.

- `knowledge/GOAL.md`: your current business goal.
- `<project>/docs/AUTHORITY.md`: the owner's dated rulings (terms, pricing rules, what copy may say). Newest rulings win.
- `<project>/docs/COPY-CANON.md`: approved wording rules.
- `<project>/docs/offers.json`: approved prices and terms.
- `<project>/docs/SERVICE-CATALOG.md`, `<project>/docs/VERTICALS.md`, `<project>/docs/POSITIONING.md`, `<project>/design/proof.json` (real results only).
- `<project>/docs/COMPARABLES.md`: which businesses count as similar, for market-intel.
- `<project>/data/intel/feed/items.jsonl`: public feed items you collect, each with a status field ("new", "digested", "skipped").
- `<project>/research/DECISIONS-CURRENT.md` and `<project>/research/LESSONS.md`: your decision log and lessons.
- A scoreboard file with your current outreach and funnel numbers, plus send and reply logs.
- `knowledge/frameworks/`: your notes on the published frameworks you want applied.
- `lessons/<agent>.md`: one lessons file per agent, append only.
- Optional: a send-hold flag file (for example `<project>/ops/state/SEND_HOLD`) that pauses all outbound work while it exists.

The agents create and maintain these themselves: `docs/CATALOG.md` and `data/catalog.json` (catalog-builder), `docs/MARKET-INTEL.md` and `data/market-intel.json` (market-intel), `docs/PLAYS.md`, `data/plays.json` and `docs/ADVISOR-LOG.md` (growth-advisor).

## Notes

The agents never send, publish or change prices. They write files and hand tasks to you or to other agents.
