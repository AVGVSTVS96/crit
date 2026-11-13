# crit

Two judges for UI work: Claude Opus through Claude Code and GPT Sol through Codex. They look at every screen of a page, top to bottom at desktop and phone width, rate how each screen looks and how well the page works, compare a before and after without knowing which is which, and rank several designs blind.

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

```sh
scripts/rank ranked/ direction-a/ direction-b/ old/   # or single screenshots
```

`review/opus.md` and `review/sol.md` hold the reviews. In a compare, `key.txt` says which folder was A. In a rank, `ranked/ranking.md` has both judges' rankings with names put back, like `direction-b >> old > direction-a`: `>` close, `>>` a clear step, `>>>` far apart.

## What's in it

- `review.md`, `compare.md` and `rank.md` are the prompts.
- `scripts/shoot` takes one screenshot per screen and writes `styles.md`, every font size, weight, family and color the page renders, so the judges can count what a screenshot only suggests.
- `scripts/judge` reviews or compares and `scripts/rank` ranks; both go through `scripts/panel`, which runs both judges at medium effort with only the screenshots and the prompt: no settings, memories, hooks, MCP servers or instruction files.
- `SKILL.md` is the loop around them: shoot, judge, check the claims, report, change, compare.

The ratings run 0 to 4: 0 broken, 1 rough, 2 stock, 3 crafted, 4 exceptional. There's no overall score, and the two judges are shown side by side, not averaged. Ratings tend to bunch at 2 and 3; to tell designs apart, rank them.

MIT licensed.
