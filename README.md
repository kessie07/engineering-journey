# Engineering Journey

This is where I keep track of what I'm building and what I'm learning.

Most of what's in here started as an experiment: a hackathon build, a challenge notebook, a Blender practice file, an idea I scaffolded at 2am and didn't get back to. Some of it turned into working software. Some of it is still rough. I wanted one place that shows all of it honestly, and that I keep updating as things move from "it works on my machine" toward software I'd actually trust other people to use.

So this isn't a finished portfolio. It's closer to a work log.

---

## Where things stand

| Project | What it is | Status | When |
| :--- | :--- | :--- | :--- |
| [RepoMind](Projects/RepoMind.md) | Ask questions about a GitHub repo. RAG over the codebase. Team project. | Built / worked on | Jul – Aug 2026 |
| [Aura](Projects/Aura-Wealth-Agent.md) | Hackathon build. Forecasts a user's balance and answers money questions in chat. | Built / worked on | Mar – Apr 2026 |
| [Amazon ML Challenge](Projects/Amazon-ML-Challenge.md) | Matching the same entity across three large datasets | Worked on (partial) | Sep 2026 |
| [DSA](Learning/DSA.md) | Relearning data structures and algorithms properly, in Python | Currently exploring | Sep 2026 – now |
| [Blender](Projects/Blender.md) | Learning 3D modelling from zero | Currently exploring | Oct 2026 – now |
| [Programming Foundations](00-Programming-Foundations/README.md) | Python basics, loops, problem-solving habits | Currently exploring | Ongoing |
| [Academic Prep](Learning/Academic-Prep.md) | My university exam notes and study tracking | Ongoing | Sep 2026 – now |
| [Kairos](Projects/Kairos.md) | Early idea around creating and remixing | Idea / early concept | Jul 2026 |
| [School Legacy](Projects/School-Legacy.md) | School / donor platform, started and paused | Idea / incomplete | Mar 2026 |
| [Automation project](Projects/Automation.md) | Not written up yet | Planned write-up | — |

What the statuses mean:

- **Built / worked on**: there's real, working code behind it, either mine or a team's I was part of.
- **Currently exploring**: I'm actively learning this. Expect early, messy work.
- **Idea / incomplete**: started, but it's mostly a scaffold or a concept right now.
- **Planned**: not started, or not documented here yet.

### Other experiments

Smaller things I built along the way that don't have their own page yet:

- **Aegis** (Nov 2025): an LLM firewall / security proxy experiment. It has a prompt classifier, a proxy app, OWASP-style security tests, a Locust load test and an ROC curve for the classifier.
- **PlacementMentor** (Feb 2026): an Arduino sketch simulated on Wokwi, plus a small Node.js "nudge" web app.

---

## Why some code isn't linked

A few of these repos are private right now. That's not because they're abandoned. I'm still fixing things, testing them, cleaning up configs and history, and I'd rather open them once they're in a state I can stand behind. Each project page says what's public and what isn't, and I'll link the code as each one is ready.

---

## How this repo is laid out

```text
engineering-journey/
├── README.md                    ← you are here
├── Projects/                    ← one page per project
├── Learning/                    ← DSA, academic prep
├── 00-Programming-Foundations/  ← first learning module (notes, journal, practice code)
├── Journal/                     ← short dated entries on what I worked on
└── Assets/                      ← screenshots and diagrams (only real ones)
```

The learning modules follow the same shape: lecture notes, an engineering handbook, an assessment, a journal, resources and practice. Not every file is filled in yet.

---

## What I'm working toward

Right now it's two things at once:

1. **Fundamentals.** Going back to Python, loops, and DSA and actually understanding them. I want to be able to reason about a problem before I touch the keyboard, not just pattern-match.
2. **Getting past the demo stage.** Most of my projects reached "it works in a demo" and stopped there. The gap between that and something reliable (deployment, tests, a frontend that doesn't break, notes on *why* a decision was made) is what I want to get better at. RepoMind's deployment to a small EC2 instance was a good lesson in exactly that.

---

## How I keep this updated

- A project page only gets deeper when I actually rebuild or learn something, not before.
- Screenshots and diagrams go in only when they're real.
- Dates and statuses get changed when things change, including when something stalls.