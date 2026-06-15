# Project 2: Air Quality Data Analysis with PartyRock

AWS AI and ML Scholars program (AWS AI Practitioner Challenge), final Project 2.

## Objective
Use AWS PartyRock's Analyze Data feature (built on Amazon Bedrock) to upload a
dataset, ask analytical questions in natural language, generate an analysis
table, and critically evaluate whether the AI's output is accurate and useful.

## Dataset
`air_quality_data.csv`: a 30-day air quality dataset (180 records, May 2026)
with columns date, time_of_day, hour, location, pm25_ugm3, pm10_ugm3, o3_ppb,
no2_ppb, co_ppm, so2_ppb, aqi. Six pollutants plus an overall AQI, sampled at
six times of day.

## What I did
1. Uploaded the dataset to partyrock.aws/data.
2. Asked three analytical questions:
   - What are the different air components recorded, and the overall average of each?
   - How does air quality change throughout the day, by time of day and ordered by hour?
   - What patterns appear over the 30 days, and does AQI differ on weekends versus weekdays?
3. Had PartyRock generate analysis tables. Behind the scenes it writes and runs
   SQL against the data, returns the result, and summarizes it in plain English.
4. Evaluated accuracy and exported the analysis table to
   `air_quality_analysis_table.csv`.

## Key findings
- Clear daily cycle: AQI is best at night (about 32) and worst at midday
  (about 60), driven by ozone peaking near 46 ppb at 1 PM (photochemical formation).
- Rush-hour spikes: PM2.5 (about 27) and NO2 (about 29) jump during the 8 AM and
  8 PM rush, then fall to about 16 at night.
- Overall 30-day averages: PM2.5 20.77, PM10 36.4, O3 26.72, NO2 21.96, CO 0.51,
  SO2 5.67, AQI 47.23 (moderate).
- The month showed cyclical, roughly week-long swings with a mid-month spike,
  not a single linear trend.

## Evaluating the AI (the important part)
PartyRock was accurate on the deterministic aggregations it could express as SQL:
the time-of-day table and the overall averages matched the data, and the tool
exposed the exact query it ran, which made the numbers easy to trust. One result
was not reliable: the weekday-versus-weekend comparison reported only 4 weekend
days in a 30-day span, when a calendar month contains roughly 8 or 9, so that
grouping miscounted and its "weekends are worse" conclusion should be discarded.
Takeaway: the tool is strong for SQL-expressible analysis, but you still have to
sanity-check the groupings and row counts rather than trusting every stated insight.

## Files
- `air_quality_data.csv`: the input dataset.
- `air_quality_analysis_table.csv`: the analysis table PartyRock generated
  (average pollutant levels and AQI by time of day).
- `REFLECTION.md`: the project reflection answers.
