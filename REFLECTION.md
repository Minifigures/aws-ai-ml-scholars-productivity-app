# Project Reflection Questions

## What does your app do? Why did you build it?

CareerProof AI takes one messy, unstructured description of my work or project experience plus a target role, and turns it into a full set of recruiter-ready materials in a single run: an experience analysis, three quantified resume bullets, a structured STAR interview answer, a portfolio blurb, a copy-paste LaTeX resume in Jake's template format, and a credibility audit. It finishes with a Jobright-style Fit Score from 0 to 100, sub-scores for skills, experience, and ATS keyword match, and a prioritized action plan that tells me what to build, what to research, and how to prepare.

I built it because two problems are real for early-career job seekers, including me. First, new grads are told to "quantify your bullets" but get stuck on how, because their experience lives in projects and internships rather than tidy corporate metrics. Second, behavioural interviews fall apart when answers ramble or stay generic. Most resume tools push you to inflate numbers and stuff keywords, which is exactly what gets exposed the moment an interviewer probes one line. I wanted the opposite: a tool that makes experience sound strong and stays defensible. That is why the Credibility Checker is the heart of the app. It flags fake-sounding metrics, vague claims, and buzzwords before a recruiter ever sees them.

## What difference did you notice between your app and using a chatbot?

The biggest difference is consistency and repeatability. With a chatbot I have to retype the same long context every time, and I get a differently shaped answer on every run, which is the "blank page" problem. CareerProof AI freezes that context into fixed input fields and fixed output templates, so I paste new experience, press play, and get the same structured seven-part breakdown every time. It is also shareable as a single public link, so anyone can use it without knowing how to prompt.

The second difference is the chaining. Each output is grounded in the previous one rather than re-derived from scratch: the resume bullets read the experience analysis, the credibility check reads the bullets, and the recommendations read all of them. That layered structure produced more reliable, less repetitive results than a single chatbot turn, and it let me assign a clear job to each step.

The most interesting thing I noticed was a limit, not a feature. When I fed the app's own cleaned-up resume back in to chase a higher score, the Fit Score did not go up, because the Credibility Checker had already stripped the buzzwords that inflate ATS keyword match. A chatbot would happily keep inflating on request. The app would not, and that honesty is the point.
