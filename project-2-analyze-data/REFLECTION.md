# Project 2 Reflection

## List 3 to 5 insights you discovered from the data
1. Air quality follows a clear daily cycle: best at night and late night (AQI about 32) and worst at midday (AQI 59.8), driven by ozone, which peaked at 46.4 ppb at 1 PM as sunlight drives its formation.
2. Particulate matter and nitrogen dioxide spiked during the morning (8 AM) and evening (8 PM) rush: PM2.5 reached about 27 ug/m3 and NO2 about 29 ppb, while both dropped to roughly 16 at night.
3. The 30-day averages were PM2.5 20.77, PM10 36.4, O3 26.72, NO2 21.96, CO 0.51, SO2 5.67, and AQI 47.23 (moderate).
4. The month showed cyclical, roughly week-long rises and falls rather than one linear trend, with a mid-month spike around May 12 to 22 and cleaner days at the start and end of the month.
5. Ozone moved opposite to the traffic pollutants: lowest at rush hour and highest at midday, the expected photochemical pattern.

## Which prompts helped you gain the best insights
Prompts that named a specific grouping and asked for a table beat general summaries. "Show the average of each pollutant and the average AQI for each time of day, ordered by hour" gave the clearest insight because it surfaced the whole daily cycle in one table. Naming the metric, the grouping dimension, and the sort order consistently produced sharper, more accurate results than open-ended questions.

## Was the AI analysis accurate
Mostly yes, with one clear exception. The time-of-day and overall-average tables were accurate and matched the real structure of the data, and the tool showed the exact SQL query it ran, which made the numbers easy to trust. The weekday-versus-weekend comparison was unreliable: it reported only 4 weekend days in a 30-day span when a month contains roughly 8 or 9, so that grouping miscounted and should not be trusted. The lesson is that PartyRock is strong for deterministic, SQL-expressible aggregations, but groupings and row counts still need a sanity check.
