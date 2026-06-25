# Startup Research — Analysis of Factors Behind Successful Acquisitions

Exploratory data analysis of startup funding, acquisitions, and founder
education data, aimed at identifying which factors are associated with
successful exits (acquisitions, IPOs) and funding outcomes.

**Notebook:** [`Startup_research.ipynb`](./Startup_research.ipynb)

---

## 1. Business Context

A venture analytics team wants to understand which company categories,
funding patterns, and founder backgrounds are associated with successful
acquisitions and funding outcomes — to better focus future investment
research.

**Goals:**
- Clean and structure raw, multi-table startup data into an analysis-ready format
- Identify the factors most associated with successful deals (acquisitions, IPOs)

**Tasks:**
- Get familiar with the data across 5 source tables
- Verify and correct data quality issues (types, missing values, duplicates)
- Perform exploratory data analysis on the merged dataset

---

## 2. Tech Stack

- **Python** (pandas, numpy)
- **Matplotlib / Seaborn** — visualizations (histograms, boxplots, bar charts)
- **phik** — non-linear correlation analysis (φK coefficient) for mixed categorical/numeric data
- **Jupyter Notebook**

---

## 3. Dataset

Five source tables, originally loaded from Yandex's training data storage:

| File | Description |
|---|---|
| `acquisition.csv` | Acquisition deals: acquiring/acquired company IDs, deal terms, price, date |
| `company_and_rounds.csv` | Company profiles merged with their funding rounds (category, funding totals, status, rounds count) |
| `education.csv` | Education records linking people to academic institutions |
| `people.csv` | Founders/employees, linked to companies |
| `degrees.csv` | Academic degree types held by each person |

**Key fields used in the analysis:**
- `funding_total`, `funding_rounds`, `status` (operating / acquired / ipo / closed)
- `category` (industry vertical: software, web, mobile, nanotech, etc.)
- `price_amount` (acquisition price)
- Education completion status per founder, derived from the people/education/degrees tables

---

## 4. Methodology

1. **Data loading & initial preprocessing** — reviewed structure of all 5
   tables, standardized column names to snake_case, checked types
2. **Cleaning & preliminary exploration** — converted date columns,
   analyzed and handled missing values, checked for duplicates, derived
   founder education-completion categories
3. **Merging & exploratory analysis** — merged company, funding, and
   acquisition data; analyzed outliers in `funding_total` (log-scale
   histograms, boxplots, percentile-based bounds); investigated
   zero/near-zero-price acquisitions; compared typical funding amounts and
   round counts across categories and exit statuses
4. **Conclusions & recommendations** — synthesized findings into
   actionable takeaways

---

## 5. Key Insights

**Industry concentration**
Among 4,365 funded companies, three categories dominate: **Software**
(784 companies), **Web** (535), and **Mobile** (396) — these represent the
largest pool of comparable deals for benchmarking.

**Funding size by category**
The highest *average* funding amounts appear in **nanotech**, **finance**,
and **enterprise** categories. However, `nanotech` is represented by only a
single company in the dataset — a result that looks dramatic but isn't
statistically reliable enough to act on directly.

**Typical funding range**
The bulk of funding amounts fall between **1M and 33M RUB**, which sets a
realistic benchmark range for typical deal sizes rather than relying on
headline-grabbing outliers.

**Funding rounds vs. exit outcome**
Companies that reached **IPO status** went through the most funding rounds
on average (~3 rounds) — more than companies that were acquired or remained
private. This suggests IPO-track companies raise more deliberately over a
longer runway, likely reflecting both investor confidence and more thorough
market preparation.

**Zero-price acquisitions**
A notable share of acquisitions were recorded at $0/$1 price despite the
acquired company having raised real funding — a pattern worth flagging
separately, as it usually signals distressed/asset acquisitions rather than
standard exits, and can distort average deal-price metrics if not isolated.

---

## 6. Recommendations

1. **Prioritize Software, Web, and Mobile** for deal sourcing — they offer
   the largest, most statistically reliable comparison pool.
2. **Treat nanotech/finance/enterprise averages with caution** — verify
   sample size before using these categories as benchmarks; single-company
   averages are not representative.
3. **Use the 1M–33M RUB range** as the realistic funding benchmark for
   typical deals, rather than outlier-driven headline figures.
4. **Track funding-round count as an IPO-readiness signal** — companies on
   an IPO trajectory consistently show more funding rounds; this could be
   a useful leading indicator for deal evaluation.
5. **Exclude $0/$1 acquisitions from average deal-price calculations**,
   or analyze them as a separate "distressed acquisition" cohort.

---

## 7. Repository Structure

```
.
├── README.md
└── Startup_research.ipynb
```

---

## Author

**Vladislav Wiesner**
[LinkedIn](https://www.linkedin.com/in/vladislav-wiesner-317048300/) · [GitHub](https://github.com/w1benz)
