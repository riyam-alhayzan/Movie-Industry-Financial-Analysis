# Movie Industry Financial Analysis

An Excel analysis of the TMDB movie dataset, examining how budget, revenue, genre and release decade relate to a film's financial performance.

**Tools:** Microsoft Excel — data cleaning, calculated columns, PivotTables, charts.

---

## Dataset

| | |
|---|---|
| Source | TMDB (The Movie Database) |
| Records | 10,173 movies |
| Fields | 22 original + 6 derived |
| Period | 1960 – 2015 |

## File

**`TMDB_Movies_Analysis.xlsx`**

| Sheet | Contents |
|---|---|
| `Raw Data` | Cleaned dataset with calculated columns |
| `Pivot & Charts` | PivotTables and bar charts |

---

## Data preparation

Cleaned copies were created rather than overwriting the source fields, so the original values stay auditable:

| Column | Treatment |
|---|---|
| `Budget_Clean` | Zero entries blanked, so they are excluded from totals and averages instead of pulling them toward zero |
| `Revenue_Clean` | Same treatment as budget |
| `Runtime_Clean` | Zero or blank runtimes replaced with the column median |

### Calculated columns

| Column | Definition |
|---|---|
| `Profit` | `Revenue_Clean − Budget_Clean` |
| `ROI_Percent` | `Profit ÷ Budget_Clean × 100` |
| `Profitable` | `Yes` / `No`, or `Unknown` where budget or revenue is missing |
| `Decade` | Release decade derived from `release_year` |

---

## Analysis

Two PivotTables, each paired with a bar chart:

1. **Total Revenue by Movie Genre**
2. **Total Revenue by Decade**

---

## Findings

### Revenue by decade

Total box office grows across every decade in the dataset and peaks in the 2000s:

| Decade | Total revenue (USD) |
|---|---|
| 1960s | 3.0 B |
| 1970s | 9.9 B |
| 1980s | 27.2 B |
| 1990s | 76.3 B |
| 2000s | 156.9 B |
| 2010s | 140.0 B |

The 2010s figure covers 2010–2015 only, so it represents a partial decade and is not directly comparable to the others.

### Profitability

Of the 3,652 films that report both a budget and a revenue figure, **2,639 (72%) turned a profit** and 1,013 did not. The remaining 6,521 records are missing at least one figure and are marked `Unknown`.

### Revenue by genre

Comedy and Drama lead on total revenue, followed by combination genres such as Comedy|Romance and Adventure|Fantasy|Action.

---

## Limitations

- Budget and revenue are missing for roughly two-thirds of the records, so the profitability findings apply only to the subset that reports both.
- Figures are nominal and not adjusted for inflation. The dataset's `budget_adj` and `revenue_adj` columns are available for an inflation-adjusted comparison.
- Genres are stored as pipe-separated combinations (`Action|Adventure|Science Fiction`), so the PivotTable groups each combination separately rather than each individual genre.
- A small number of records carry an invalid release year and fall outside the named decades.

