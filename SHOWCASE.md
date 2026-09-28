# CareerProof AI: Sample Run

A real end-to-end run, to show what the chained outputs produce.

> **Check every figure against the raw input.** The app's outputs can contain figures and details the model made up. In this run, everything marked **[not in input]** below appears in none of the inputs: the 40-minute and 5-minute timings, the 87% reduction, tournament bracket generation, and the date and location in the LaTeX heading. The heading's job title is the target role, not a job the user held, so it is marked **[not in raw experience]**. Treat any output as a draft and remove or correct every claim you cannot back up before it goes on a resume.

**Inputs**

- **Target Role:** Frontend / Full-Stack Developer Intern. React, Next.js, TypeScript, building user-facing web apps and dashboards used by real users. Bonus: shipping real products end-to-end and owning features.
- **Your Raw Experience:** "i made the website for my university billiards club from scratch, next.js react typescript. like 320 members use it. i built an elo ranking system that pulls from a google sheet, and a thing where you take a photo of the paper match sheet and it reads the names and winner automatically using a vision AI api ... not sure how to make this sound impressive on a resume."
- **Focus and Tone:** Software Engineering

## Recommendations and Action Plan (Jobright-style metrics)

```
FIT SCORE: 82
Near-perfect technical match for the role, and 320 real users on a solo-built
production app is a genuine differentiator. Credibility issues in the framing
and the absence of a public portfolio link are what hold the score below 90.

Skills Match: 92%
Experience Match: 74%
ATS Keyword Match: 78%
```

The same experience scored 52 against a fintech backend role (Python and AWS gaps), which shows the Fit Score adapts to how well the experience matches each specific role.

## Resume Bullet Generator

> Architected and shipped a full-stack club management platform in Next.js, React, and TypeScript as sole developer, serving 320 users with live ELO rankings, tournament bracket generation **[not in input]**, and an AI-powered match entry system.

> Engineered a Vision AI pipeline that parses photos of handwritten match sheets and extracts player names and results, cutting per-session data entry from roughly 40 minutes to under 5 minutes **[not in input]**.

## Credibility Checker (excerpt)

> "Vision AI API" is not a product name. It sounds like marketing language. Interviewers will ask which one. Fix: name the actual tool, for example "Google Cloud Vision API."

> "active users" implies you instrumented activity tracking. The honest claim is "320 registered members," which is what your notes actually say.

## Resume in LaTeX (Jake's Template)

```latex
%-----------EXPERIENCE-----------
\section{Experience}
\resumeSubHeadingListStart
  \resumeSubheading
    {Frontend / Full-Stack Developer Intern}{Present} % [not in raw experience: this is the target role, not a job held] [not in input: date]
    {Club Management Platform Project}{Remote} % [not in input: location]
    \resumeItemListStart
      \resumeItem{Architected and shipped a full-stack club management platform in Next.js, React, and TypeScript as sole developer, serving 320 users with live ELO rankings, tournament bracket generation, and an AI-powered match entry system.} % [not in input: tournament bracket generation]
      \resumeItem{Engineered an automated match entry feature using a Vision AI API to parse photos of handwritten score sheets, reducing per-session data entry from 40 minutes to under 5 minutes, an 87\% reduction.} % [not in input: 40 minutes, 5 minutes, 87%]
    \resumeItemListEnd
\resumeSubHeadingListEnd
```

The LaTeX output is copy-paste ready for Jake's Resume template, with placeholder comments for the Education and Projects sections when those optional inputs are left blank.
