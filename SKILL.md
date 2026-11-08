---
name: crit
description: Get an honest read on a visual design from two independent judges, Claude Opus through Claude Code and GPT Sol through Codex. Use to check UI work before calling it done, on a web page or on screenshots of an app.
---

# crit

Two judges review the same screenshots with the same plain prompt, `review.md`, and score each screen and the whole. Each sees only the screenshots and the prompt, so what they say is their own read.

1. **Screenshots.** For a web page, `scripts/shoot <url> <dir>` captures the whole page one screen at a time, at 1440px and 390px wide (needs [agent-browser](https://github.com/vercel-labs/agent-browser)). For an app, put its screenshots in a folder, named in the order they should be read.
2. **Judges.** `scripts/judge "<url or what it is>" <dir> <out-dir>` runs both at once and writes `opus.md` and `sol.md`. It takes a few minutes.
3. **Report.** Give each judge's overall score and biggest points, where they agree and where they split. Pass their verdicts on as they wrote them: they're there to see what the builder can't.

The judges get the screenshots and `review.md`, nothing else. What changed, what the page is for, or what you hope to hear would steer them.
