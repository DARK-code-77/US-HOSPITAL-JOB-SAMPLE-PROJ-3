# US Hospital Jobs: Data Analysis & Dashboard

An end-to-end, portfolio-ready analysis of a sample of US hospital job postings. The project uses Python and pandas to inspect, clean, and enrich the data; a Jupyter notebook documents the analysis; and a standalone HTML dashboard lets readers explore posting patterns interactively.

## Project contents

```text
.
├── CODE.ipynb
├── dashboard.html
├── README.md
├── us-hospital-jobs-sample.csv
└── outputs/                         # created when the notebook is run
    ├── cleaned_hospital_jobs.csv
    ├── posting_overview.png
    └── postings_by_date.png
```

## Dataset at a glance

The supplied sample contains **17,557 job postings** and 15 original columns, including job title, health system, system state and bed count, location, department, employment type, posting date, salary fields, application URL, and source platform. In this sample, posting dates range from **October 10 through October 17, 2026**.

Notable data-quality considerations:

- Salary fields are blank for **11,800 postings (about 67%)**. Salary analysis must use only listings with usable pay data.
- Department is not specified for many postings, and employment-type labels have inconsistent capitalization and spacing.
- `system_state` describes the health system's state field; it should not automatically be treated as the job's physical work state. Use `location` when interpreting a specific job location.
- Listings are a snapshot. A posting count is not a measure of hires, open positions over time, or market share.

## Getting started

### 1. Set up Python

Python 3.9+ is recommended. Install the packages used by the notebook:

```powershell
python -m pip install pandas numpy matplotlib jupyter
```

### 2. Run the analysis

Keep `CODE.ipynb` and `us-hospital-jobs-sample.csv` in the same folder, then start Jupyter:

```powershell
jupyter notebook
```

Open `CODE.ipynb` and run all cells from top to bottom. The notebook creates `outputs/cleaned_hospital_jobs.csv` and refreshes the embedded dashboard data in `dashboard.html`.

### 3. Open the dashboard

Open `dashboard.html` in a modern browser. It works offline and includes the supplied dataset snapshot; no web server or JavaScript chart package is required. Use the dropdown filters to explore states, health systems, job families, and employment types. Rerun the notebook after replacing the CSV to refresh the dashboard.

## Analysis workflow

1. Load and inspect the source data and column types.
2. Measure missing values and check for duplicate records.
3. Standardize text, dates, numeric salary fields, and employment-type labels.
4. Engineer job-family, title-length, posting-date, bed-size, and salary-availability features.
5. Compare postings by state, health system, job family, employment type, source, and posting date.
6. Review salary coverage and summarize available salaries without combining unlike pay periods.
7. Export the cleaned data and refresh the self-contained dashboard.

Missing values are not filled with invented salary or department data. The notebook retains the original salary columns and adds explicit features for salary availability and valid salary midpoint. No posting is removed except a duplicate identified by its application URL.

## Dashboard

The dashboard includes interactive KPI cards and charts for:

- Postings by health-system state and health system
- Job-family and employment-type mix
- Source-platform distribution
- Posting-date distribution
- Salary data availability

All charts are rendered locally in the browser. The notebook refreshes the data embedded in the HTML, so the dashboard is easy to share as a standalone file.

## Important interpretation notes

- Job-family labels are rule-based categories inferred from job-title text; they are useful for broad exploration, not definitive occupational classifications.
- Salary values may use different currencies and pay periods. Compare them only within matching currency and period groups.
- `system_beds` describes the health-system size field in the source; it is not necessarily the number of beds at the specific job location.
- Verify the original data's collection method, update date, and redistribution permissions before publishing the CSV or making claims beyond this sample.

## Tools

Python · pandas · NumPy · Matplotlib · Jupyter · HTML · CSS · JavaScript
