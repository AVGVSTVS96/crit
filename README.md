# crit

Two judges for UI work: Claude Opus through Claude Code and GPT Sol through Codex. They look at every screen of a page, top to bottom at desktop and phone width, rate how each screen looks and how well the page works, and compare a before and after without knowing which is which.

```sh
npx skills add AVGVSTVS96/crit
```

It needs `claude` and `codex` signed in, and [agent-browser](https://github.com/vercel-labs/agent-browser) for screenshots.

## By hand

```sh
scripts/shoot https://example.com before/
scripts/judge "a product's home page" "find out what it is and get started" review/ before/
# change the page, then
scripts/shoot https://example.com after/
scripts/judge "a product's home page" "find out what it is and get started" compare/ before/ after/
```

`review/opus.md` and `review/sol.md` hold the reviews. In a compare, `key.txt` says which folder was A.

## What's in it

- `review.md` and `compare.md` are the two prompts.
- `scripts/shoot` takes one screenshot per screen and writes `styles.md`, every font size, weight, family and color the page renders, so the judges can count what a screenshot only suggests.
- `scripts/judge` runs both judges at medium effort with only the screenshots and the prompt: no settings, memories, hooks, MCP servers or instruction files.
- `SKILL.md` is the loop around them: shoot, judge, check the claims, report, change, compare.

The ratings run 0 to 4: 0 broken, 1 rough, 2 stock, 3 crafted, 4 exceptional. There's no overall score, and the two judges are shown side by side, not averaged.

MIT licensed.
