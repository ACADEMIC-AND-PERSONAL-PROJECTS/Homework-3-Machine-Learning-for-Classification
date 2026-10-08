<div align="center">

<!-- HERO BANNER -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1a1a2e,30:16213e,70:0f3460,100:1a1a2e&height=300&section=header&text=HW3%20:%20Classification&fontSize=38&fontColor=ffffff&animation=twinkling" width="100%"/>

<!-- TYPING INTRO -->
<img src="https://readme-typing-svg.demolab.com/?font=Fira+Code&size=16&pause=1000&color=00d4ff&center=true&vCenter=true&width=600&lines=Machine+Learning+Zoomcamp+2026;DataTalks+Club;Homework+3+-+Logistic+Regression+%26+Feature+Elimination&center=true" alt="Typing SVG" />

</div>

<!-- TECH ICONS -->
<p align="center">
<img width="40" height="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python" />
<img width="40" height="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/numpy/numpy-original.svg" alt="NumPy" />
<img width="40" height="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/pandas/pandas-original.svg" alt="Pandas" />
<img width="40" height="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/matplotlib/matplotlib-original.svg" alt="Matplotlib" />
<img width="40" height="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/scikitlearn/scikitlearn-original.svg" alt="Scikit-Learn" />
<img width="40" height="40" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jupyter/jupyter-original.svg" alt="Jupyter" />
<img height="40" src="https://img.shields.io/badge/Optuna-hyperparameter%20optimization-3B4CCA?style=flat-square" alt="Optuna" />
</p>

---

<!-- ABOUT -->
### About

Third assignment of the **Machine Learning Zoomcamp 2026** organized by **DataTalks Club**. You can enroll in the course here: [courses.datatalks.club/ml-zoomcamp-2026](https://courses.datatalks.club/ml-zoomcamp-2026/).

This project covers **classification** with logistic regression for lead scoring. We explore missing value imputation, correlation analysis, mutual information for feature selection, one-hot encoding, feature elimination, and regularization with different `C` values.

On top of the assignment, a **personal continuation** retrains the model on the full training set, evaluates it with a classification report & confusion matrix, and runs an **Optuna** hyperparameter search — pushing test accuracy from **0.67 → 0.73**.

The **course_lead_scoring_2026.csv** dataset contains 5,000 lead records (source, industry, employment status, location, income, courses viewed, interactions, lead score) and the target `converted` telling whether the lead signed up to the platform.

<div align="center">

<img src="avatar.png" width="736" alt="Avatar"/>

</div>

---

<!-- STATS BAR -->
<table>
<tr>
<td align="center" width="120">

**5K**
Rows

</td>
<td align="center" width="120">

**8**
Features

</td>
<td align="center" width="120">

**6**
Questions

</td>
<td align="center" width="120">

**0.645**
Val Accuracy

</td>
<td align="center" width="120">

**0.73**
Test Acc (Optuna)

</td>
</tr>
</table>

---

<!-- QUESTIONS -->
### Homework Questions

<table>
<tr>
<td width="50%">

#### Q1 - Q2 : Exploration & Correlation

- **Q1** : Mode of `industry` (`technology`)
- **Q2** : Biggest correlation (`interaction_count` & `lead_score`)

</td>
<td width="50%">

#### Q3 - Q4 : Mutual Information & Baseline Model

- **Q3** : Highest mutual information (`lead_source` : 0.03)
- **Q4** : Validation accuracy (`0.65`)

</td>
</tr>
</table>

<table>
<tr>
<td width="50%">

#### Q5 - Q6 : Feature Elimination & Regularization

- **Q5** : Least useful feature (`number_of_courses_viewed` : diff 0.002)
- **Q6** : Best `C` (`C = 0.001` : accuracy 0.645)

</td>
<td width="50%">

#### Key Takeaways

- `lead_source` is the most informative categorical feature
- Removing `interaction_count` hurts accuracy the most (0.044)
- Stronger regularization (smaller `C`) lowers accuracy

</td>
</tr>
</table>

---

<!-- KEY CONCEPTS -->
### Key Concepts

<table>
<tr>
<td width="33%">

#### Data Preparation
- Categorical missing → `'NA'`
- Numerical missing → `0.0`
- Correlation matrix heatmap

</td>
<td width="34%">

#### Feature Selection
- Mutual information score
- One-hot encoding (`handle_unknown='ignore'`)
- Feature elimination (drop-one)

</td>
<td width="33%">

#### Logistic Regression
- `solver='liblinear'`, `max_iter=1000`
- Accuracy metric
- Regularization with `C`

</td>
</tr>
</table>

---

<!-- STRUCTURE -->
### Project Structure

```
HW3/
├── course_lead_scoring_2026.csv   # Dataset (5K leads)
├── notebook.ipynb                 # Notebook with solutions + Optuna continuation
├── pyproject.toml                 # Project configuration
├── avatar.jpg / avatar.png        # Avatar (source / rounded, used in README)
├── higuruma.jpg / higuruma.png    # Continuation banner (source / rounded)
└── README.md
```

---

<!-- SETUP -->
### Installation

```bash
# Clone the repo
git clone <repo-url>
cd HW3

# Install dependencies (with uv)
uv sync

# Launch the notebook
uv run jupyter notebook notebook.ipynb
```

---

<!-- DATASET PREVIEW -->
### Dataset Preview

| lead_source | industry | employment_status | location | annual_income | number_of_courses_viewed | interaction_count | lead_score | converted |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| organic_search | technology | employed | europe | 88160 | 3 | 4 | 0.64 | 1 |
| social_media | technology | employed | south_america | 72688 | 3 | 7 | 0.72 | 1 |
| referral | retail | employed | europe | 44697 | 3 | 4 | 0.58 | 1 |
| paid_ads | manufacturing | student | NA | 0.0 | 3 | 6 | 0.57 | 0 |
| referral | manufacturing | student | north_america | 24062 | 4 | 5 | 0.62 | 1 |

---

<!-- RESULTS -->
### Results Summary

| Question | Answer | Detail |
|:---:|:---:|:---|
| Q1 | `technology` | Most frequent value in `industry` (1173 rows) |
| Q2 | `interaction_count` & `lead_score` | Highest correlation among the proposed pairs |
| Q3 | `lead_source` | Mutual information `0.03` (rounded to 2 decimals) |
| Q4 | `0.65` | Accuracy on the validation set |
| Q5 | `number_of_courses_viewed` | Smallest difference `0.002` (0.6450 → 0.6430) |
| Q6 | `0.001` | Best `C`, validation accuracy `0.645` |

---

<!-- CONTINUATION -->
### Beyond the Homework — My Own Continuation

<div align="center">

<img src="higuruma.png" width="735" alt="Higuruma — JJK"/>

</div>

**Not part of the assignment.** After Q6 I kept going and reused the skills already covered in class.

#### 1 — Retrain on the full training set
Training + validation merged → **4 000 rows**, evaluated once on the untouched **1 000-row test set**
(`classification_report` + seaborn confusion matrix).

| Model | Accuracy |
|:---:|:---:|
| Homework model (`C = 0.001`, retrained) | **0.67** |
| Optimized model (Optuna) | **0.73** |

#### 2 — Optimization with Optuna
100 trials maximizing validation accuracy over:

- `C` — log-scaled from `1e-6` to `10`
- `solver` — `liblinear` / `lbfgs` / `newton-cholesky`
- `class_weight` — `None` / `balanced`

**Best trial** → `C = 1.186`, `solver = newton-cholesky`, `class_weight = None` — validation accuracy **0.731**

*The homework grid picked the strongest regularization (`C = 0.001`), while Optuna found that a much weaker regularization (`C ≈ 1.19`) generalizes better — a nice reminder that a hand-picked grid is only as good as the values you thought to test.*

---

<!-- FOOTER -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f3460,50:16213e,100:1a1a2e&height=100&section=footer" width="100%"/>

**Machine Learning Zoomcamp 2026 -- DataTalks Club**

</div>
