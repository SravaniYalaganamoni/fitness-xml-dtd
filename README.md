# Fitness App XML + DTD

## Contents
- `fitness.dtd` – rules for user profile and workouts
- `sample.xml` – valid XML (should PASS)
- `broken.xml` – invalid XML (should FAIL with clear reasons)
- `validate.ipynb` – simple lxml validator (Colab-friendly)

---

## Framework

### Decision
Track and reason about personal training load: what I did, when, how intense, and key metrics—so I can adjust volume and avoid over/under-training.

### Signals (5–7)
1. **Date** of workout
2. **Kind** (`run`, `walk`, `cycle`, `strength`, `yoga`, `swim`)
3. **Duration** (minutes)
4. **Intensity** (`low`, `moderate`, `high`)
5. **Distance** (km for cardio, optional)
6. **Calories** (kcal, optional)
7. **Metrics** (avg/max heart rate, steps)

### Gaps
- DTD can’t enforce numeric types or ISO dates; those are conventions.
- No weekly aggregates (e.g., training load, VO₂ estimates).
- No device provenance (watch/phone) or GPS tracks.

### Risk
- Wrong/stale data skews training load decisions.
- Enum drift (e.g., `extreme`) breaks validation.
- Missing `id` prevents unique referencing.

### Stewardship
- **Owner:** Me
- **Where:** GitHub (PRs for edits); optional backup in cloud drive
- **Retention:** Current semester + 1 term for portfolio reuse

### Data Domain
- **Primary:** Fitness Workouts
- **Adjacent:** Health Metrics / Nutrition

---

## How to Validate
Open `validate.ipynb` in Google Colab, upload (or clone) the repo, and run.
Expected: `sample.xml` = PASS, `broken.xml` = FAIL with error lines.
