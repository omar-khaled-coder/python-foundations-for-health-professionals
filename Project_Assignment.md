# Project Assignment — Python Foundations for Data Science

**M.Sc. Digital Health — Data Analytics** / M.Sc. Business Analytics
Module: Python Foundations for Data Science
Lecturer: Dr. Jenny Delekta
Semester: SuSe 2026
Weight: **100 % of the module grade**
Submission deadline: **Monday, 18 May 2026, 23:59 CEST**
Submission: single Jupyter notebook (`.ipynb`) uploaded to **AC5**
 **or** a zip-Folder with your data included.
---

## 1. What this project is, and why it exists

The goal of this practical work is to demonstrate that you can use Python to take a real dataset from its raw, imperfect state to a small, defensible analytical conclusion — and present that journey in a notebook that another reader can follow and trust.

The point is **not** to produce a sophisticated model or a publication-grade study. The point is to show that you can:

- formulate a question that data can plausibly answer;
- load real data and make it analysable;
- compute one meaningful summary and one informative figure;
- write code that another person can read and run;
- reflect honestly on what you did and what you would do differently.

If you have followed the five sessions and the Wednesday tutorial, you have everything you need to do this well. It is a small, focused piece of work — realistically around **30 short cells** — not a thesis. A good submission is concise: each cell does one thing, and the notebook reads as a short narrative.

> A note on context. The in-class worked example uses a hospital operations dataset (Saint Mary's) because the module is formally part of the Digital Health programme. The course is, however, attended predominantly by **Business Analytics** master students, and the methods are domain-agnostic. Your project will use a dataset and a topic of your own choosing — sales, customer behaviour, finance, marketing, operations, HR, sports, environment, or anything else where the data tell a story. The code patterns from the hospital example translate one-to-one. Examples in this brief therefore use a generic **sales / orders** context that maps cleanly to business work; adapt the variable names to your own data.

---

## 2. What you must submit

A single Jupyter notebook with the following properties:

| Requirement | Detail |
|---|---|
| **File format** | `.ipynb` |
| **Filename** | `surname_firstname_python_project.ipynb` (use ASCII characters only — replace umlauts, e.g. `mueller_jenny_python_project.ipynb`) |
| **Submission channel** | **AC5** (Python Foundations course area) |
| **Self-contained** | The notebook must run top to bottom on a fresh kernel without errors. Restart kernel → Run All → no red cells. |
| **Data attached or linked** | If your dataset is small, include the CSV alongside the notebook in a zip. If it is large or publicly available, include a markdown cell with the URL and the date you downloaded it. |
| **Reproducibility** | Anyone with your notebook and your data file (or the link) must be able to reproduce your result. |

> A notebook that does not run end-to-end on a clean kernel will be marked as if every cell after the first failing one were absent. Please run it once on a restarted kernel before you submit.

---

## 3. Choosing your dataset

You choose your own dataset. Recommended sources, organised by typical topic area:

**Broad catalogues (any topic)**
- **Kaggle** — `https://www.kaggle.com/datasets` (the largest open catalogue; filter by topic)
- **UCI Machine Learning Repository** — `https://archive.ics.uci.edu/` (classic curated datasets)
- **OpenML** — `https://www.openml.org/` (cross-domain, with metadata)
- **Google Dataset Search** — `https://datasetsearch.research.google.com/` (federated search)

**Business, finance, economics**
- **FRED — Federal Reserve Economic Data** — `https://fred.stlouisfed.org/` (macroeconomic and financial time series)
- **World Bank Open Data** — `https://data.worldbank.org/` (economic, social, environmental indicators)
- **Eurostat** — `https://ec.europa.eu/eurostat/data/database` (European economic and social statistics)
- **Yahoo Finance** (via `yfinance` Python package) — historical stock prices
- **Online retail and customer-behaviour datasets on Kaggle** — search for "retail", "ecommerce", "customer", "churn", "marketing"

**Health, environment, social, sports**
- **WHO Global Health Observatory** — `https://www.who.int/data/gho`
- **OECD Data** — `https://data.oecd.org/`
- **OurWorldInData** — `https://ourworldindata.org/` (curated indicators)
- **Sports-reference / FBref / NBA stats / Football-data** — for sports analytics

**Your own data**
- If you have something from work, a side project, a public-facing dashboard at your employer, or a hobby (running tracker, music listening history, weather station, etc.), that is more than welcome — and often makes the reflection more meaningful.

Constraints on your choice:

| Constraint | Why |
|---|---|
| **Minimum 50 rows, minimum 4 columns** | Enough that the aggregation and plot say something meaningful |
| **At least one categorical column and one numeric column** | So that groupby and visualisation are both possible |
| **Some imperfection is welcome** | Missing values, inconsistent labels, an outlier or two — real data is rarely clean, and dealing with imperfection is part of what is being assessed. If your dataset is already pristine, that is fine, but do not artificially break it. |
| **Topic of interest to you** | You will spend several hours with it — choose something you do not mind looking at |
| **Avoid datasets that are pre-cleaned tutorial examples** | The Iris dataset and the Titanic dataset have been analysed by every learner of the past decade; pick something less familiar |

A business, finance, marketing, or operations topic is the natural fit for most of you. Health, environment, social, or sports topics are equally welcome. The criterion is *substantive interest*, not topic.

---

## 4. Required notebook structure

The notebook should follow this order. The names of the sections may differ; the order should not.

### 4.1 Title cell — Markdown

A single markdown cell at the very top, containing:

- Project title
- Your full name
- Your matriculation number
- The date of the submission

### 4.2 Question cell — Markdown

State, in one paragraph:

- the **question** you are asking (one specific question, not three vague ones);
- **why** it matters, or what would change if you knew the answer;
- **what an answer would look like** if you had it — a number, a comparison, a ranking, a curve.

> A good test of a clear question: can you state it in one sentence that ends with a question mark, and can you describe the answer in another sentence? If yes, your question is well-scoped.

Example of a clear question (business):
*Among the transactions in the 2023 online-retail dataset, do customers in northern European countries place higher-margin orders than those in southern Europe, and does this difference depend on the product category?*

Example of a clear question (health, for comparison):
*Among encounters in the Saint Mary's dataset, do older patients (≥ 65) have longer lengths of stay than younger patients, and does this differ by ward?*

Example of an unclear question:
*What is interesting about this dataset?*

### 4.3 Imports cell — Code

A single code cell with all your `import` statements:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from pathlib import Path
```

Place every import here, not scattered throughout the notebook.

### 4.4 Data source cell — Markdown

A markdown cell describing:

- where the data come from (URL or file path);
- what the rows represent (one row = one patient? one encounter? one country-year?);
- the number of rows and columns;
- a brief note on any peculiarities you know in advance (encoding, special markers for missing values, etc.).

### 4.5 Loading and inspection — Code + Markdown interleaved

- Load the data with `pd.read_csv` (or `read_excel` / `read_json` / etc., as appropriate).
- Inspect: `.shape`, `.dtypes`, `.head()`, `.isna().sum()`, `.duplicated().sum()`, and `value_counts()` on a relevant categorical column.
- After inspection, write a short markdown cell summarising what you found: how many rows, how many missing values where, anything unexpected.

### 4.6 Cleaning — Code + Markdown interleaved

- Address types (e.g. parse dates), duplicates, missing values, and inconsistent string labels — to the extent that your data require.
- **Before each cleaning step, write a one-sentence markdown cell explaining why you are doing it.** "Convert `admission_date` to a datetime so that monthly resampling becomes possible" is enough — but the *why* must be there.
- If your data are already clean, write a markdown cell stating which checks you performed and what you found.

### 4.7 Transformation — Code

- Derive at least one new column from the existing ones.
- Apply at least one filter (a boolean mask).
- Sort the table in a way that makes sense for your question.

### 4.8 Aggregation — Code + Markdown

- Apply at least one `groupby` producing a summary table.
- Display the result.
- Write a one-paragraph markdown cell interpreting the summary in plain language.

### 4.9 Visualisation — Code

- Produce at least one plot — a bar chart, a line chart, a histogram, a boxplot, or a scatter plot, as appropriate to your question.
- The plot must have a **title**, **axis labels with units**, and a **legend if it carries multiple series**.
- Save the figure to a PNG file with `plt.savefig(...)` before `plt.show()`.

### 4.10 Reflection — Markdown

A final markdown cell of three short paragraphs:

1. **What you learned** — name one or two things that became clearer through this project.
2. **What was hardest** — be specific. "The cleaning was hard" is too vague; "Aligning my date column with the calendar of the staffing file was hard because the formats differed" is useful.
3. **What you would do differently next time** — one or two improvements.

This is not a place to be modest or self-deprecating. It is a place to be specific and honest. Two well-chosen sentences are worth more than a paragraph of generalities.

---

## 5. Required micro-skills (sprinkled throughout)

In addition to the structural requirements above, your notebook must contain **at least one occurrence of each** of the following ten micro-skills. They may appear wherever they fit naturally — there is no requirement to dedicate a section to them, but each must be present and visible. A short markdown note above the relevant cell is recommended so that the grader can identify it.

> Each item is worth approximately 1–2 points of the readability grade. Missing items count against the readability score, not against correctness.

### M1 — Read a single value by its index

Use `.loc` or `.iloc` to read one specific value (one cell) from your DataFrame. Print it. Add a comment naming what you just read.

```python
# Order total of the transaction in row 5
order_total_row_5 = df.loc[5, "order_total"]
print(order_total_row_5)

# OR, by label (if order_id is the index):
df.set_index("order_id").loc["ORD-00042", "order_total"]
```

### M2 — Aggregate a NumPy array sensibly

Convert one column to a NumPy array (`.to_numpy()`) and compute at least **two** summary statistics with NumPy functions (e.g. `np.mean`, `np.median`, `np.std`, `np.percentile`). State in a one-line comment why the two are different (or why they are close).

```python
order_values = df["order_total"].to_numpy()
mean_value   = np.mean(order_values)
median_value = np.median(order_values)
print(f"mean = {mean_value:.2f}, median = {median_value:.2f}")
# The mean exceeds the median, which suggests right-skew driven by a few very large orders.
```

### M3 — Build a boolean mask and use it twice

Construct a boolean mask once and use it in two different ways: once to count rows, once to filter the DataFrame.

```python
high_value = df["order_total"] >= 1000
print(f"{high_value.sum()} of {len(df)} orders exceed 1000 EUR")
high_value_df = df[high_value]
```

### M4 — Apply a vectorised operation

Derive a new column from existing ones using column arithmetic — no Python `for`-loop over the rows.

```python
df["margin_eur"] = df["revenue_eur"] - df["cost_eur"]
```

### M5 — Use a list comprehension

Build a list using `[expr for x in ...]` somewhere in the notebook. A common occasion is to construct a list of colours for a bar plot, or a list of labels.

```python
colors = ["red" if v < 0 else "green" for v in df["margin_eur"]]
```

### M6 — Define one function with a docstring

Define at least one function that performs a re-usable step. Give it a docstring describing what it does. Call it at least once.

```python
def order_size_band(amount):
    """Return a categorical size band for an order amount in EUR."""
    if amount < 100:    return "small"
    if amount < 1000:   return "medium"
    return "large"

df["size_band"] = df["order_total"].apply(order_size_band)
```

### M7 — Verify a merge with `validate=`

If you merge two DataFrames, use the `validate=` argument and a short markdown cell explaining the cardinality you asserted (`"1:1"`, `"1:m"`, `"m:1"`).

```python
# Each order references exactly one product; each product appears in many orders: m:1.
enriched = orders.merge(product_catalog, on="product_code", how="left", validate="m:1")
```

If your project does not naturally call for a merge, write a markdown cell explaining why a merge would have been inappropriate.

### M8 — Handle missing values explicitly for at least one column

Pick one column with missing values. State in a markdown cell whether you decided to drop the rows, drop the column, impute, or let `NaN` propagate, and why. Implement the decision and verify it (`isna().sum()` before and after).

If your dataset has no missing values, write a markdown cell stating that you checked and found none.

### M9 — Use an f-string to produce a one-line summary

At one point in the notebook — ideally in the aggregation or reflection section — print a one-line summary of a finding using an f-string.

```python
print(f"The North region shows the highest mean margin at {mean_north:.2f} EUR, "
      f"compared to {mean_other:.2f} EUR for the other regions combined.")
```

### M10 — Comment your code with intent, not paraphrase

Every code cell should have at least one comment that explains *why* a line exists, not what it does verbatim. The Python is the *what*; the comment is the *why*.

```python
# Bad: this line subtracts cost from reimbursement
df["margin_eur"] = df["reimbursement_eur"] - df["cost_eur"]

# Good: a positive margin means the DRG payment covered the case cost
df["margin_eur"] = df["reimbursement_eur"] - df["cost_eur"]
```

---

## 6. Grading rubric

| Criterion | Weight | What earns full marks | What loses marks |
|---|---|---|---|
| **Clarity of the question** | 20 % | One specific question, motivated, with a clear notion of what an answer looks like | Vague topic statement; multiple unrelated questions; no motivation |
| **Data preparation** | 20 % | Loading and cleaning steps are documented and each decision is justified in a markdown cell | Cleaning happens silently; defaults applied without justification; data are not actually clean after the cleaning section |
| **Correctness of the analysis** | 30 % | The aggregation and the plot answer the question stated; the calculations are correct; the visual is readable | The analysis does not address the question; calculation errors; the plot lacks labels or misleads |
| **Readability and structure** | 20 % | Logical cell order; meaningful names; functions where appropriate; comments explain intent; all ten micro-skills present | Spaghetti notebook; opaque names; copy-pasted blocks; missing micro-skills |
| **Reflection** | 10 % | Specific, honest, useful — names a concrete difficulty and a concrete improvement | Generic ("I learned a lot"); apologetic; absent |

A correctly reasoned analysis that reaches a partially wrong answer is worth more than a correct answer reached without visible reasoning. We grade the journey, not only the destination.

---

## 7. Practical tips

- **Restart kernel and Run All before submitting.** This is the single most common cause of lost marks. Do it the evening before. Then do it once more in the morning.
- **Comment your code as you write it, not after.** Comments written retrospectively tend to describe the code rather than the intent.
- **Less is more.** A focused 30-cell notebook that answers one question well is better than a sprawling notebook of three times the length that wanders. Quality beats quantity, and each cell should do one identifiable thing.
- **If something does not work, leave a markdown cell explaining what you tried and why you moved on.** Honest dead ends are not penalised; pretending nothing happened is.
- **The workflow reference (`Workflow_Messy_CSV_to_Report.html`) is your friend.** It lists every command you are likely to need with an explanation. Use the search bar (Ask).
- **Use the worked example as a template** for cell structure, not for content. Copying the Saint Mary's analysis is not acceptable; using its scaffolding is.

---

## 8. AI usage policy

Use of AI tools (ChatGPT, Copilot, Claude, Gemini, etc.) is permitted as a support tool, subject to the following:

1. You must be able to **explain every line** of your notebook. The oral defence at submission may include questions about specific cells; "the AI wrote it" is not an answer.
2. If you used AI for syntax help — say so in the reflection cell. One sentence: *"I used ChatGPT to suggest an approach for handling the multi-index after the aggregation; the implementation is mine."*
3. Blind copying of AI-generated cells without understanding is treated as a serious academic-integrity issue.
4. Code that runs without you knowing why is worth zero marks on the readability axis, regardless of where it came from.

The spirit of the rule: AI is a tutor you can ask, not a ghost-writer you can hire. If you can explain it, you can use it.

---

## 9. Where to get help before the deadline

- **Wednesday tutorial, 13 May 2026, evening** — optional, online. Bring your notebook in whatever state it is in. We will work through your specific problems live.
- **Workflow reference** — `Workflow_Messy_CSV_to_Report.html` (open in any browser). The Ask button accepts plain-English questions.
- **Course cheat sheets** — `NumPy_Pandas_Reference_Block_B.pdf`, `Python_Reference_Block_B.pdf`, `Terminology_Cheat_Sheet_v2.pdf`.
- **AC5 course area** — check there for clarifications and FAQs; post your questions, other students likely have the same one.
- **Email** — for questions that are personal rather than technical.

A note on timing: please do not wait until Sunday evening!

---

## 10. Final checklist before you submit

Tick each item before uploading:

- [ ] Filename follows the convention (`surname_firstname_python_project.ipynb`)
- [ ] Kernel restarted, all cells run without error
- [ ] Title cell with name, matriculation number, and date
- [ ] One specific question, stated as a single sentence ending with a question mark
- [ ] Imports gathered at the top
- [ ] Data source documented (URL or file path, row × column count, brief description)
- [ ] At least one cleaning decision justified in a markdown cell
- [ ] At least one derived column
- [ ] At least one `groupby` (or `pivot_table`) with interpretation
- [ ] At least one labelled plot saved to disk
- [ ] All ten micro-skills (M1–M10) present
- [ ] Reflection cell — specific, honest, three short paragraphs
- [ ] Notebook size focused — around 30 short cells, each doing one identifiable thing

---


