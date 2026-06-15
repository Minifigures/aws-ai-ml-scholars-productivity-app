# AWS AI and ML Scholars: Hands-on Projects

My two final hands-on projects from the AWS AI Practitioner Challenge (AWS AI and
ML Scholars program), both built on AWS PartyRock, an app and analysis layer on
top of Amazon Bedrock.

- **Project 1: CareerProof AI** (detailed below): a generative-AI productivity
  app that turns messy experience into recruiter-ready resume bullets, STAR
  answers, a LaTeX resume, and a Jobright-style fit score, with a credibility
  check. Built with a 7-step prompt chain.
- **Project 2: Air Quality Data Analysis**: using PartyRock's Analyze Data
  feature to query a 30-day dataset, generate an analysis table, and critically
  evaluate the AI's output. See [`project-2-analyze-data/`](project-2-analyze-data/).

---

## Project 1: CareerProof AI

**An AI career-prep assistant built on AWS PartyRock (Amazon Bedrock).** It turns messy, unstructured work and project experience into recruiter-ready career materials through a multi-step prompt chain, then audits its own output for credibility and tells you exactly what to do next.

**Live app (public):** https://partyrock.aws/u/Minifigures/gBGjeULT_/CareerProof-AI%253A-Transform-Experience-Into-Results

Built for the AWS AI and ML Scholars program (Project: Build Your First AI Productivity App).

> Author: Marco Anthony Ayuste

---

## The problem it solves

Two pain points are well documented for early-career job seekers:

1. **Quantifying experience.** New grads know online tools tell them to "quantify your bullets," but they get stuck on how, because their experience is in projects, internships, and part-time work rather than tidy corporate metrics.
2. **Telling the story.** In behavioural interviews, candidates ramble, spend most of the answer on setup, or give generic answers that prove nothing.

Most resume tools also push you to inflate numbers and stuff keywords, which backfires the moment an interviewer probes a single line.

CareerProof AI takes one raw description of what you did and produces a quantified resume, a structured STAR interview answer, a portfolio blurb, and a copy-paste LaTeX resume, then runs a **credibility audit** that flags inflated metrics, vague claims, and buzzwords before a recruiter ever sees them.

---

## What it does

**Inputs (5)**

- **Target Role or Job Description** (paste a title or the full posting)
- **Your Raw Experience** (rough notes, any format)
- **Focus and Tone** (dropdown: Software Engineering, AI and ML, Data, Product and Business, Internship)
- **Education (optional)** (acts as a reusable profile field)
- **Key Projects (optional)** (acts as a reusable profile field)

An always-visible **Input Examples and Formats** guide keeps the expected formatting on screen even while you type.

**Chained outputs (7)**

1. **Experience Analyzer** extracts skills, tools, quantifiable impact, leadership, and missing proof, aligned to the target role.
2. **Resume Bullet Generator** writes 3 bullets in the form "Accomplished X by doing Y, resulting in Z," tailored to the role.
3. **STAR Interview Story** restructures the same experience into Situation, Task, Action, Result.
4. **Portfolio Blurb** writes a short project card for a personal site.
5. **Credibility Checker** audits the generated bullets and flags fake-sounding metrics, vague claims, missing numbers, and overhyped AI buzzwords, with specific fixes.
6. **Recommendations and Action Plan** produces a Jobright-style **Fit Score (0 to 100)** plus Skills Match, Experience Match, and ATS Keyword Match sub-scores, then a prioritized action plan (gaps to close, what to build, what to research, how to prep).
7. **Resume in LaTeX (Jake's Template)** outputs a copy-paste-ready resume section using the popular Jake's Resume LaTeX macros.

---

## How it works (architecture)

Every output is a separate Amazon Bedrock prompt template, and the widgets are wired into a **dependency graph** so each step is grounded in the previous one rather than re-deriving from scratch. This is prompt chaining, and it reduces hallucination because the Resume Bullet Generator reads the Experience Analyzer, the Credibility Checker reads the bullets, and the Recommendations widget reads all of them.

```
Inputs: Target Role, Raw Experience, Focus and Tone, Education, Key Projects
   |
   v
Experience Analyzer
   |
   +--> Resume Bullet Generator --> STAR Interview Story
   |                            \--> Portfolio Blurb
   |                            \--> Resume in LaTeX (Jake's Template)
   |                            \--> Credibility Checker
   |                                       |
   +---------------------------------------+--> Recommendations and Action Plan (Fit Score)
```

PartyRock sits on top of Amazon Bedrock and handles the API orchestration and scaling, so the work is in designing the prompts, the variable injection, and the chain, not the infrastructure.

---

## Why a structured app beats a chatbot

A chatbot makes you retype the same long context every time and gives you a different shape of answer on every run. CareerProof AI freezes that context into reusable input fields and fixed output templates, so it is consistent, shareable by link, and repeatable. Paste new experience, press play, and get the same five-part, recruiter-ready breakdown every time.

---

## Design principle: credibility over keyword-stuffing

In testing, feeding the app's own cleaned-up bullets back in did not inflate the Fit Score, because the Credibility Checker strips buzzwords and undefendable metrics. That is intentional. A higher ATS number is not worth a bullet that collapses under one interview follow-up. The app optimizes for claims you can defend.

---

## Roadmap: from MVP to a real product (saved profiles and RAG)

This PartyRock app is the **MVP** that validates the AI logic. PartyRock is stateless, so a published app cannot store a per-user profile across sessions. The optional Education and Key Projects fields act as a "fill-once, reuse" profile for the owner's own use, but true per-user persistence needs a real backend.

The productionization path, modelled on Jobright, Simplify, and Workday autofill:

- **Saved profile fields:** contact info, work experience, education, skills, links, and role and location preferences, plus a master resume.
- **Memory and RAG:** a vector store over the user's profile and past answers so the app personalizes outputs and reuses prior answers to unique questions.
- **Stack:** Next.js, React, and TypeScript on the front end, Supabase (Postgres) with Auth for accounts and profile storage, and a vector index for retrieval. Optionally Amazon Bedrock for the model layer to keep parity with this MVP.

Sequence: PartyRock MVP first (done), then rebuild as a Next.js plus Supabase plus Auth app with a saved profile and RAG.

---

## Tech and concepts

Amazon Bedrock, AWS PartyRock, foundation models, prompt engineering, prompt chaining, multi-step AI workflow design, variable injection, model orchestration, zero-shot generation.

---

## Project 2: Air Quality Data Analysis

Using PartyRock's Analyze Data feature (Amazon Bedrock) to query a 30-day air
quality dataset, generate an analysis table, and critically evaluate the AI's
output. Full writeup and files: [`project-2-analyze-data/`](project-2-analyze-data/).

**What it covers**
- Uploaded a 30-day dataset (180 records, six pollutants plus AQI) and asked 3
  natural-language questions. PartyRock writes and runs SQL behind the scenes,
  then summarizes the result.
- Found a clear daily cycle: AQI is best at night (about 32) and worst at midday
  (about 60) from peak ozone, with PM2.5 and NO2 spiking at the morning and
  evening rush.
- Generated and exported an analysis table of average pollutant levels and AQI by
  time of day.
- Critically evaluated the AI: the time-of-day analysis was accurate and the tool
  showed the exact SQL it ran, but the weekday-versus-weekend comparison
  miscounted weekend days (4 in a 30-day span), so that insight was unreliable.
  The takeaway is that the tool is strong for SQL-expressible aggregations but
  still needs a sanity check on groupings and row counts.

## License

All Rights Reserved. See [LICENSE](LICENSE). This is a proprietary showcase: the code, prompts, and text may not be copied, modified, or reused without written permission. Copyright protects this specific implementation; it does not stop independent ideas, which is why the repo is a public portfolio piece rather than an open-source template.
