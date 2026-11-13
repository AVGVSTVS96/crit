---
name: crit
description: Review a UI with two independent judges, Claude Opus through Claude Code and GPT Sol through Codex, then check what they say and compare before and after a change. Use on a web page or app screenshots before calling UI work done.
---

# crit

```text
shoot → judge → check → report → change → compare
```

1. **Shoot.** `scripts/shoot <url> <dir>` screenshots the whole page one screen at a time at 1440px and 390px, and writes `styles.md`: every font size, weight, family and color it renders. For an app, put its screenshots in a folder in reading order, and a `styles.md` if you can get one.
2. **Judge.** `scripts/judge "<what it is>" "<what people come to do>" <out> <dir>` runs both judges at medium effort and writes `opus.md` and `sol.md`. They get the screenshots, `styles.md` and `review.md`, nothing else: no settings, memories or instruction files. Say what people come to do in their words, and keep out what changed or what you hope to hear.
3. **Check.** Hold each claim that matters against the screenshots, `styles.md` and the source. Drop what doesn't hold; mark what screenshots can't settle.
4. **Report.** Lead with the verdict. Put both judges' ratings side by side and show where they split rather than averaging. Then the checked findings, biggest first, each with its screenshot attached. Show the screenshots, not just text.
5. **Change.** Fix up to three related findings, then shoot again.
6. **Compare.** `scripts/judge "<what it is>" "<what people come to do>" <out> <before> <after>` shows both versions as A and B in a random order; `key.txt` says which is which. Record better, same, worse or can't tell, and anything that got worse.

Stop after three rounds, or sooner when another round has nothing concrete to gain.
