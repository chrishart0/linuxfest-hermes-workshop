# Agenda — 45-Minute Workshop Draft

## Frame

Build your first daily intelligence agent with Hermes.

Story-first, build-focused. The agenda should create emotional buy-in, then move quickly into the workshop guide.

Detailed material lives elsewhere:

- Objective / positioning: [`docs/workshop-objective.md`](workshop-objective.md)
- Attendee activity: [`docs/workshop-guide.md`](workshop-guide.md)
- Default project prompt: [`examples/prompts/daily-intelligence-agent.md`](../examples/prompts/daily-intelligence-agent.md)
- Template skill: [`examples/skills/daily-intelligence-report/SKILL.md`](../examples/skills/daily-intelligence-report/SKILL.md)

## Definition of done

Attendees succeed if they leave with:

- Hermes installed and working in the CLI
- a model/provider connected
- one Daily Intelligence Report skill bootstrapped for something they actually care about

Cron, gateway delivery, PDF, Telegram, Discord, and email are stretch goals.

## Agenda spine

### 1. Opening loop — agents beyond coding

Purpose: make the room feel why this matters before setup friction begins.

Core beat:

> Coding agents proved the pattern. Today is about using open-source tooling to build agents that work for you outside the editor.

Open loops to create:

- What comes after coding agents?
- What does a real non-coding agent do every day?
- Why is relevance more valuable than summarization?
- Can I start one in this session?

### 2. Real examples — this is not hypothetical

Purpose: credibility and emotional buy-in, built around one held open loop.

Sequence — quick teasers first, then artifact, then reveal:

1. personal daily intelligence briefing (teaser)
2. release-watch/check-in agent (teaser)
3. personal health reporting (teaser)
4. **the 8:03 artifact** — this morning's redacted money report from team Discord.
   Read it out loud, pause, then: "nobody on the team wrote this." Let the room
   sit with *then who did?* Do not explain yet.
5. **reveal Ana** — the team's business analyst as a Hermes profile: read-only on
   production, 8 cron jobs, 23 custom skills she edits herself from feedback
6. **close the loop into the build** — day-one Ana ≈ what attendees build today;
   she was useful ~3 hours after her profile was created

Must land:

> The magic is not summarization. The magic is relevance.

> Ana went from new profile to answering live revenue questions in one evening —
> with the same ingredients you'll use today.

### 3. The pattern

Purpose: give the mental model without duplicating the workshop guide.

Pattern:

```text
sources + your world + relevance filter + skill + report + feedback
```

Must land:

> Do not just summarize the internet. Cross-reference it against your world.

### 4. Expectations

Purpose: reduce pressure.

Say:

> If you leave with Hermes working and one Daily Intelligence Report skill bootstrapped, you succeeded. If you also get cron, PDF, Telegram, Discord, or email working, wonderful — I’ll help with that tonight.

### 5. Open the workshop guide

Purpose: transition from talk to doing.

Attendees use:

[`docs/workshop-guide.md`](workshop-guide.md)

Do not duplicate setup commands here. The guide owns the commands.

### 6. Start the default project

Purpose: core hands-on work.

Default path:

[`examples/prompts/daily-intelligence-agent.md`](../examples/prompts/daily-intelligence-agent.md)

That prompt points to the template skill:

[`examples/skills/daily-intelligence-report/SKILL.md`](../examples/skills/daily-intelligence-report/SKILL.md)

The live objective is to bootstrap the skill and generate the first useful report if time allows.

### 7. Improve once with feedback

Purpose: close the “self-improving” loop honestly.

Must land:

> Self-improvement starts with feedback, not magic.

The attendee gives the first report feedback, then Hermes edits the skill itself.

### 8. Next layers and evening help

Purpose: show the path forward without making it required.

Mention only as next layers:

- cron
- gateway delivery
- PDF
- Telegram / Discord / email
- richer data sources
- multiple focused skills feeding one final briefing

Close:

> If you do not finish now, that is okay. I’ll be around tonight to help wire cron, Telegram, Discord, local data, weird servers, whatever.

Final line:

> Make Hermes read the boring stuff for you — and give you the version worth acting on.
