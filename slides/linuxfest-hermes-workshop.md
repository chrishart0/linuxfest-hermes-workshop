---
marp: true
size: 16:9
paginate: true
header: ''
title: 'Build Your First Useful Agent with Hermes'
author: Chris Hart
description: A practical, LinuxFest workshop for building a Daily Intelligence Agent with Hermes.
---

<!--
SPEAKER NOTE (deck-wide):
45-minute slot, Saturday 10:00 AM. Audience is terminal-first, open-source, self-hosting.
Lead with respect for their existing skills. The agent is a new tool on the shelf next to
cron, ssh, and grep — not a replacement for thinking. Demos carry the talk; slides are scaffolding.
-->

<style>
:root {
  --bg:        #0b0e14;
  --bg-panel:  #131820;
  --bg-code:   #0e131b;
  --border:    #2a3140;
  --fg:        #e6edf3;
  --muted:     #93a1b0;
  --accent:    #6cc59a;   /* calm terminal green */
  --accent-2:  #5cb0c6;   /* muted cyan */
  --accent-3:  #d8a657;   /* warm amber, used sparingly */
  --danger:    #e07a6b;
}

section {
  background: var(--bg);
  color: var(--fg);
  font-family: -apple-system, "Inter", "Segoe UI", "Helvetica Neue", sans-serif;
  font-size: 26px;
  line-height: 1.45;
  padding: 56px 72px;
  letter-spacing: 0.1px;
}

/* subtle dotted grid texture, very low contrast */
section::after {
  content: '';
  position: absolute;
  inset: 0;
  background-image: radial-gradient(var(--border) 0.6px, transparent 0.6px);
  background-size: 28px 28px;
  opacity: 0.18;
  pointer-events: none;
}

h1 { font-size: 56px; font-weight: 700; color: var(--fg); margin: 0 0 12px; letter-spacing: -0.5px; }
h2 { font-size: 38px; font-weight: 650; color: var(--fg); margin: 0 0 20px; letter-spacing: -0.2px; }
h3 { font-size: 27px; font-weight: 600; color: var(--accent); margin: 0 0 8px; }
h2 strong, h1 strong { color: var(--accent); }

p, li { color: var(--fg); }
strong { color: var(--fg); font-weight: 650; }
em { color: var(--accent-2); font-style: normal; }
a { color: var(--accent-2); text-decoration: none; }
ul, ol { margin-top: 4px; }
li { margin: 8px 0; }
li::marker { color: var(--accent); }

code {
  font-family: "JetBrains Mono", "Fira Code", "SF Mono", ui-monospace, monospace;
  background: var(--bg-code);
  border: 1px solid var(--border);
  border-radius: 5px;
  padding: 1px 7px;
  font-size: 0.82em;
  color: var(--accent);
}
pre {
  background: var(--bg-code);
  border: 1px solid var(--border);
  border-left: 3px solid var(--accent);
  border-radius: 8px;
  padding: 22px 26px;
  font-size: 20px;
  line-height: 1.5;
  box-shadow: 0 6px 24px rgba(0,0,0,0.35);
  overflow: visible;
}
pre code { background: none; border: none; padding: 0; color: var(--fg); font-size: 1em; }

blockquote {
  border: none;
  border-left: 3px solid var(--accent-2);
  background: var(--bg-panel);
  border-radius: 0 8px 8px 0;
  margin: 8px 0;
  padding: 16px 26px;
  color: var(--fg);
  font-size: 0.95em;
}
blockquote strong { color: var(--accent-2); }

table {
  border-collapse: collapse;
  font-size: 0.86em;
  width: 100%;
  margin-top: 6px;
}
th, td { border: 1px solid var(--border); padding: 13px 18px; text-align: left; color: var(--fg); }
td { background: var(--bg-panel); }
td strong { color: var(--accent); }
th { background: #1b222d; color: var(--accent); font-weight: 600; }

header { color: var(--muted); font-size: 14px; letter-spacing: 1px; text-transform: uppercase; }
footer { color: var(--muted); font-size: 13px; letter-spacing: 0.4px; opacity: 0.8; }
section::before { } /* reserved */
section { --paginate-color: var(--muted); }
section:after { } 

/* ---- utility classes ---- */
.kicker {
  color: var(--accent);
  font-family: "JetBrains Mono", ui-monospace, monospace;
  font-size: 18px;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 10px;
}
.muted { color: var(--muted); }
.big { font-size: 1.25em; }

/* lead / title slides */
section.lead { justify-content: center; }
section.lead h1 { font-size: 64px; }
section.lead .sub { color: var(--muted); font-size: 28px; margin-top: 18px; }
section.lead .meta {
  margin-top: 40px; color: var(--muted); font-size: 20px;
  font-family: "JetBrains Mono", ui-monospace, monospace;
}

/* two-column flex */
.cols { display: flex; gap: 36px; align-items: flex-start; }
.cols > * { flex: 1; }

/* card grid */
.grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-top: 8px;
}
.card {
  background: var(--bg-panel);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 20px 24px;
}
.card h3 { margin: 0 0 6px; font-size: 22px; }
.card p { font-size: 18px; color: var(--muted); margin: 0; line-height: 1.4; }
.card .tag {
  font-family: "JetBrains Mono", ui-monospace, monospace;
  font-size: 13px; color: var(--accent-2); letter-spacing: 1px;
}

/* timeline */
.timeline { font-family: "JetBrains Mono", ui-monospace, monospace; font-size: 21px; }
.timeline .row { display: flex; gap: 18px; align-items: baseline; padding: 9px 0; border-bottom: 1px solid var(--border); }
.timeline .row:last-child { border-bottom: none; }
.timeline .t { color: var(--accent); white-space: nowrap; min-width: 92px; }
.timeline .now { color: var(--accent-3); white-space: nowrap; min-width: 92px; }
.timeline .lead-txt { color: var(--fg); }
.timeline .muted { color: var(--muted); }

/* router: full-width "what you babysit → which track" mapping */
.router { margin-top: 14px; }
.router .row {
  display: flex; align-items: center; justify-content: space-between;
  gap: 28px; padding: 17px 4px; border-bottom: 1px solid var(--border);
}
.router .row:last-child { border-bottom: none; }
.router .sym { color: var(--fg); font-size: 25px; }
.router .track {
  font-family: "JetBrains Mono", ui-monospace, monospace;
  font-size: 23px; color: var(--accent); font-weight: 600; white-space: nowrap;
}
.router .track .n { color: var(--accent-2); }

/* the mental-model line */
.modelline { font-size: 30px; line-height: 1.7; }
.modelline b { color: var(--accent); }

/* checklist */
.check li::marker { content: '✓  '; color: var(--accent); }
.x li::marker { content: '✕  '; color: var(--danger); }

/* prompt label bubble for demo slides */
.demo-pill {
  display: inline-block;
  background: rgba(108,197,154,0.12);
  border: 1px solid var(--accent);
  color: var(--accent);
  font-family: "JetBrains Mono", ui-monospace, monospace;
  font-size: 15px; letter-spacing: 1px;
  padding: 4px 14px; border-radius: 999px; margin-bottom: 14px;
}
</style>

<!-- _paginate: false -->
<!-- _class: lead -->
<!-- _footer: '' -->

# Build Your Own **Useful Agents**


<div class="meta">github.com/chrishart0/linuxfest-hermes-workshop</div>

<!--
OPENING (0:00). Keep slides light; talk over them.
Start with coding agents as the familiar proof point, then widen the frame: if agents can inspect repos, run tools, and iterate, what else can they do for the rest of your work?
-->

---

<!-- _class: lead -->

<div class="kicker">The question</div>

# Coding agents are only the **first** obvious use case.

<div class="sub">What happens when you point the same pattern at your servers, dashboards, newsletters, releases, inboxes, and calendar?</div>

<!--
Suggested beat from docs/workshop-objective.md:
Agents can write code, inspect repos, run tests, and iterate. That use case is locked in. Today is about applying the same shape outside the editor.
-->

---

<!-- _class: lead -->

# This is not hypothetical

<div class="sub">How I am using agents for business and personal use cases</div>

<!--
Set up four quick examples. Do not over-explain yet; each gets its own slide.
The story is credibility and desire: this is already useful in real personal/business workflows.
-->

---

<!-- _class: lead -->

# Personal daily briefing

<div class="sub">Tools, AI news, local events, business signals, and things worth acting on.</div>

<!--
Talk track: one PDF / report that reads the sources you already check every morning and pulls out what matters.
Examples: tools/software news, newsletters/blogs, local events, business news, local news.
-->

---

<!-- _class: lead -->

# Ops Agent: Release Monitoring and Triage

<!--
This is the strongest emotional proof. Tell the live release story: the agent surfaced customer-impacting analytics issues quickly enough to squash bugs and draft apology/remediation emails.
-->

---

<!-- _class: lead -->

# Health

<div class="sub">Personal health, blood work / labs, fitness tracker metrics</div>

---

<!-- _class: lead -->

<div class="kicker">8:03 AM · team Discord · #reports</div>

> $xxxx gross on 123 orders. Biggest movement: gross down 5% vs yesterday
> even though orders were up — AOV slipped. Refund flow down 2%.

<div class="kicker">8:10 PM  · team Discord · #reports</div>

> @Founder serious customer-sat issue: support has 16 customer threads sitting 4h+ without a reply today, including 10 refund/cancel threads. That is the live leak.

<div class="sub">Nobody on the team wrote this.</div>


---


![bg contain](assets/ana-architecture-diagram.png)


---

## Analyst agent: day one → today

- **Useful in ~3 hours.** Created in one evening; answering live revenue questions
- **Paid for itself on day one.** Flagged that the analytics dashboard was over-counting a KPI vs the database. 

> **Day-one Ana is roughly today's build:** a profile, a one-sentence job, read-only access to data, daily iterations via discord

<!--
All three facts came from interviewing Ana herself, who pulled them from session history.
This is the bridge slide — land the closing line hard: nobody in this room is 23 skills away from value; they are one evening away.

-->

---

## Hermes mental model

<div class="modelline">

**Memory** helps Hermes *know you.*
**Skills** help Hermes *know how.*
**Cron** and **webhooks** tell Hermes *when to act.*
**Gateway** puts the result *where humans already are.*

</div>

<!--
You've already seen all four running — that's Ana.

Keep this four-line model intact everywhere. It is still the portable Hermes frame.
Connect it back to today's build: we start with a skill; cron/gateway are stretch layers.
Callback: Ana is all four lines at full size — memory = the business definitions and pitfalls, skills = her 23 custom workflows, cron = her 8 scheduled reports, gateway = Discord where the team lives.
-->

--- 

# Workshop guide

github.com/chrishart0/linuxfest-hermes-workshop/blob/master/docs/workshop-guide.md

## Checklist

✅ Setup your LLM Inference (Open Router, Codex, GitHub Copilot, Claude, ...)
✅ Install Hermes
✅ Configure Hermes with a model
✅ Test Hermes, say hi
✅ Follow `examples/prompts/daily-intelligence-agent.md` to setup your agent

### Stretch Goal

✅ Configure a gateway, hermes sends your repots and chats where you are (Discord, telegram, etc)
