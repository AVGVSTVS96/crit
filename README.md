# crit

A design review panel for coding agents. Two judges, Claude Opus 5.5 through Claude Code and GPT-6.1 Sol through Codex, look at every screen of a page or app and score it against the best work they know.

Agents that build UI tend to pass their own work. crit gives them a second look that reads the whole page, not just the first screen, and tells a borrowed style from a crafted one.

## Install

```sh
npx skills add AVGVSTVS96/crit
```

Then ask Claude Code to crit a page or a folder of screenshots. It needs `claude` and `codex` logged in, and `agent-browser` to screenshot web pages.

## Run it by hand

```sh
scripts/shoot https://example.com shots/
scripts/judge https://example.com shots/ review/
```

`review/opus.md` and `review/sol.md` hold the two reviews.

## How it works

- `review.md` is the whole prompt. It asks for a visual review screen by screen, a score per screen on a scale where 5 is ordinary competent work and 10 is the best the judge knows, what the look takes from a style or trend, and an overall score.
- `scripts/shoot` takes one screenshot per screen height, top to bottom, at desktop and phone widths, so both judges see the same images.
- `scripts/judge` runs both judges at medium effort with only the images and the prompt: Opus gets just the Read tool, and Sol runs with its shell, skills, plugins and memories turned off.

MIT licensed.
