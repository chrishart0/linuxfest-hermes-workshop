# Workshop Objective

## Locked objective

Build your first useful agent with hermes. We will start with a daily intelligence agent, since that is achievable in 45m.

Make Hermes read the stuff you already read every morning, cross-reference it against what you actually run, manage, attend, or care about, and bubble the most important things to the top.

This is something I have multiple iterations of running every day, both for personal and business. You can do it too.

## Core thesis

The magic is not summarization. The magic is relevance.

The opening should create tension, not just explain. Open these loops early and close them through the workshop:

1. Coding agents are only the first locked-in use case. If agents work for code, what else can they work for?
2. The presenter is using this every day in production and personal workflows. What are those agents actually doing?
3. One agent caught real customer-impacting issues during a live release. How did it know what mattered, and how did it help?
4. Attendees can leave with the start of one themselves. How can that be possible in 45 minutes?
5. The trick is not summarization. Then what is the trick?

Close those loops by showing the daily intelligence pattern: sources, the attendee's world/context, relevance filter, report format, delivery, and feedback.

Suggested opening language:

> You have all seen the AI agent hype. Many of you have probably used coding agents — Codex, Claude Code, OpenCode, Cursor, whatever. That use case is locked in. Agents can write code, inspect repos, run tests, and iterate.
>
> But coding is only the first place agents got good enough to feel real.
>
> The question I want to open today is: what happens when you point that same pattern at the rest of your work?
>
> Your servers. Your logs. Your newsletters. Your releases. Your dashboards. Your support inbox. Your calendar. Your health metrics. Your business metrics.
>
> I am not talking about something theoretical. I have Hermes agents doing this every day — for my own life and for real production products. One of them recently watched a live feature release, surfaced customer-impacting issues from analytics, and helped me respond faster than I could have by staring at dashboards.
>
> By the end of this session, you will understand the pattern, and you will have the start of one yourself.
>
> We are going to build the first version of a daily intelligence agent: something that reads the information you already check every morning, cross-references it against your world, and bubbles the important stuff to the top.
>
> The magic is not summarization. The magic is relevance.

## Secondary thesis

Do not just summarize the internet. Cross-reference it against your world.

## Audience promise

By the end of 45 minutes, attendees should have:

1. Hermes installed.
2. A model/provider connected.
3. One daily intelligence agent project started.
4. A first useful report generated, or at minimum a reusable source/filter/report prompt ready to run.

### Stretch goals
5. Have 1 Hermes gateway configured so you get your report where you will actually see it

## What the agent can read and cross-reference

- Distro/tool/software news.
- GitHub releases and changelogs.
- CVEs/security advisories.
- Newsletters/blogs/RSS they already read.
- Homelab/server status.
- Production monitoring, alerts, and metrics.
- Personal context like events, local news, health metrics, schedule, and projects.

## Example stories to weave in form present's actual use

1. Daily agregator newsletter that gives me 1 PDF with
   - Tools/software news: What changed in the tools I actually use? 
     - Even goes over what people are talking about on X.com in my space to enrich new release news
   - Newsletter/blog aggregation
      - Read what I already subscribe to and pull out what matters to me.
   - Looks for networking event and just fun stuff to do around town, makes me a calendar
   - Business news that may be useful for my business
   - Local news I may care about

2. Production monitoring daily report
   - What happened across my live product app while I was away?
   - Knows about ongoing activies, like deploy of a big new feature, so can specificlly watch for issues
      - Example: big release, we temp setup 30m checkins, then moved to 4h. This was wildly succesful, as it was surfacing live issues customer were experincing, recorded in our analytics, then I was squashing bugs as fast as it was detecting users having them. The agent even drafted emails for me to send to the specfic users to apoligize and remediate. One of the best experinces I've had recently. Really felt like a live teammate and moved so fast.

3. Business Key Metrics report
   - Surfaces most important numbers, like revenue, refunds, etc
   - Highlights anything which looks odd

4. Support and feedback report
   - Reads through our live support emails
   - Reading through our products built in feedback system to surface important feedback
   - Watches analytics to look for problems users may be experiencing


### Other example that aren't from my use but would be cool
2. CVEs/sysadmin relevance
   - Which of today's CVEs matter for my actual machines?



5. Newsletter/blog aggregation
   - Read what I already subscribe to and pull out what matters to me.

## Positioning

This is not a generic news bot.

It is an agent that turns your morning information diet into a personalized intelligence report.

## Minimum excellent session

The session shape is:

1. Story — make attendees want the thing by showing real daily intelligence agents in use.
2. Pattern — explain the reusable shape: sources, user context, relevance filter, report format, delivery, feedback.
3. Install — get Hermes installed, connected to a provider, and smoke-tested.
4. Build — start one daily intelligence agent for something the attendee actually cares about.
5. Next layers — show how the same agent can later be scheduled and delivered through cron, gateway, PDF, Telegram, Discord, or email.

## Core definition of done

If an attendee leaves with Hermes working and a reusable daily intelligence prompt for something they actually care about, they succeeded.

If they also get cron, gateway delivery, PDF, Telegram, Discord, or email working, that is a stretch win.

## Teaching posture

This is story-first, build-focused, and humane about finishing later.

Use the default Hermes setup path in the workshop. Do not make Docker/container setup part of the live flow. It can be mentioned as a more isolated/security-conscious option, but 45 minutes is too short for that complexity.

The test is simply running local Hermes in the CLI after install/provider setup.

Say explicitly: if attendees do not finish in 45 minutes, that is okay. The goal is to get the agent started. The presenter will be available in the evening or hangout room to help finish cron, delivery, Telegram, Discord, local data sources, or other setup.

## Tiny trust/safety beat

Start read-only. Require sources and evidence. Do not let the agent act until it has earned trust.
