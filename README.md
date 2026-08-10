# Vestibular schwannoma growth probability

A single-page research calculator. It estimates the probability of at least 20% tumour
volume growth from baseline, measured at a surveillance scan roughly one to three years
later, from a baseline volume, one follow up volume, and the interval between them.
Age and sex are optional inputs.

The page is entirely self contained. There is no server, no analytics, and no network
request of any kind. Everything you type stays in your browser.

## Model

Extremely randomised trees, 300 trees of depth 2, trained on 91 patients from a single
centre with 28 growth events.

| | Patients (events) | AUC | Sensitivity | Specificity |
|---|---|---|---|---|
| Held out test | 31 (10) | 0.81 | 0.80 | 0.67 |
| External validation | 32 (9) | 0.71 | 0.67 | 0.56 |

The algorithm was chosen by repeated nested cross validation on training data alone,
where it had the tightest seed to seed spread of seven candidates. It was not chosen on
the test or external results. `model.json` holds the same model as data, for anyone
wanting to re-implement it.

## Not a medical device

Research use only. Developed on 91 patients with 28 events and externally validated on
32 patients with 9 events, so confidence intervals are wide. At the operating threshold
roughly half of flagged patients do not go on to grow. It has not been prospectively
validated, cleared by any regulator, or assessed for any effect on patient outcomes. It
must not replace radiological or clinical assessment.
