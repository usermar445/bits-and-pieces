# Design von Experimenten

## Diversion
Pay attention to: 

- unit of diversion: cookie? user-id? etc. depends on technicalities
- consistency of diversion: diversion should be consistent, e.g. if change on multiple sites, then unit of diversion needs to be persistent
- ethical considerations: security and confidentiality questions
- Variability: if unit of diversion (e.g. cookie) is different from unit of analysis (e.g. click-through-rate = clicks/page views), then variability is likely to be much higher; therefore use empirically computed variability, because if e.g. cookie-based, events no longer independent

## Population
Different approach: intra-user experiment or interleaved experiment; but mainly: inter-user experiment

Choose population: target in advance, e.g. same geo-location, etc.

**Cohort**  
Define entering class, e.g. entered experiment at same time or other information (regular users, etc.)

Cohohrt vs. population: cohorts harder to analyze, because you will lose users; but used more when looking for stability, e.g. learning effect, etc.

## Size
Steps: 

- check possible unit of diversion and analysis
- decide on practical significance you want
- calculate standard error analytically and compare to empirical
- get size of experiment and decide


## Duration
Pay attention: 

- Do days differ? Weeks? Seasonality?
- Exposure: risky changes should be limited


