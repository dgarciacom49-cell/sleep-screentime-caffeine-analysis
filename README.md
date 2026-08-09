# Screen Time, Caffeine, and Sleep Quality as Predictors of College GPA

## Overview
This project investigates whether daily smartphone screen time and caffeine
intake predict undergraduate GPA, controlling for sleep quality. Data was
collected via an original Qualtrics survey (n = 30) and analyzed in R.

## Research Question
Do daily smartphone screen time and daily caffeine intake predict college
students' academic performance (GPA), when controlling for sleep quality?

## Method
- **IV1 — Screen Time:** Self-reported daily smartphone use (hours/day),
  excluding phone calls
- **IV2 — Caffeine Intake:** Self-reported beverage servings, converted to
  total daily caffeine (mg) using standard published values per beverage
  type
- **Control — Sleep Quality:** Pittsburgh Sleep Quality Index (PSQI), a
  validated 19-item instrument scored using the official 7-component
  algorithm (subjective quality, latency, duration, habitual efficiency,
  disturbances, medication use, daytime dysfunction)
- **DV — GPA:** Self-reported cumulative GPA (4.0 scale)
- **Analysis:** Multiple linear regression (GPA ~ Screen Time + Caffeine +
  PSQI Global Score)

## Key Findings
- The model explained **74% of the variance in GPA** (R² = .741,
  adjusted R² = .712), F(3, 26) = 24.84, p < .001
- **Screen time significantly predicted lower GPA** (b = -0.064, p < .001),
  even after controlling for caffeine and sleep quality
- **Sleep quality (PSQI) significantly predicted lower GPA** (b = -0.040,
  p = .026)
- **Caffeine intake was not a significant predictor** of GPA once screen
  time and sleep quality were accounted for (p = .190) — its bivariate
  correlation with GPA (-0.52) appears to be explained by its overlap with
  screen time and sleep quality rather than an independent effect

## Notable Data Challenges
- Built a full PSQI scoring pipeline from raw survey responses, replicating
  the validated 7-component algorithm (not a simple averaged scale)
- Wrote a custom time-parsing function in R to standardize inconsistent
  free-text bed/wake time entries (e.g., "11:45", "9:40 AM", "12:00AM")
  into usable sleep-efficiency calculations, including handling overnight
  time wraparound
- Applied a log transformation to correct right-skewed caffeine intake data
- Conducted a reliability check (Cronbach's alpha) on the PSQI disturbance
  subscale

## Tools
R (tidyverse, psych), Qualtrics

## Files
- `Project_Analysis.Rmd` — full analysis script (data cleaning, PSQI
