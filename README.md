# Indian Startup Funding Data Analysis + Scraping from StartupTalky

This project is a complete data analysis pipeline that scrapes startup funding data from [StartupTalky](https://startuptalky.com), cleans and standardizes the dataset, and extracts deep insights on investor activity, sector trends, and funding patterns.

---

## Project Features

- Scrape live startup funding data  
- Standardize messy data (currencies, sectors, locations)  
- Analyze top investors, sectors, and ticket sizes  
- Prepare cleaned dataset for use in dashboards or ML  
- Output actionable business intelligence  

---

## Data Sources

- Website: [StartupTalky - Indian Startup Funding](https://startuptalky.com/tag/funding-news/)
- Scraped using `requests`, `BeautifulSoup`, and stored in structured CSV format

---

## Messy Aspects:

- Inconsistent currency symbols (₹, Rs, INR, $, USD)

- Amounts written in formats like "10 crore", "5M", "1.2 million", etc.

- Investor names in one string, separated by commas or inconsistent delimiters

- Missing or partial date information

---

## Tasks:

- Standardize funding amounts

- Normalize investor lists

- Extract year-wise/sector-wise trends

---

## Dataset Columns

| Column Name       | Description                                 |
|-------------------|---------------------------------------------|
| `Company`         | Name of the startup                         |
| `Sector`          | Startup business domain                     |
| `Headquarters`    | Startup's city/state/country                |
| `Amount`          | Raw funding string (e.g. "$2M", "₹100 Cr")  |
| `Funding Round`   | Seed, Series A, etc.                         |
| `Lead Investors`  | List of investors                           |
| `Month`, `Year`   | Funding time                                |
| `Amount_INR`      | Standardized amount in INR                  |

---

## Data Cleaning and Enrichment

### Funding Amount Normalization
- Parses complex strings like: `Rs 100 crore`, `USD 2 million`, `Rs 10 crore (~$1.2M)`
- Converts all amounts to INR using a consistent exchange rate (e.g., 1 USD = ₹83)
- Stores final numeric value in `Amount_INR`

### Sector Cleanup
- Merges similar sector labels:
  - `FinTech`, `finance technology` → `fintech`
  - `EdTech`, `education` → `education`
- Supports startups tagged with multiple sectors

### Lead Investor Breakdown
- Splits multiple investors using `,` and `&`
- Identifies:
  - Most active investors
  - Average ticket size
  - Sector-wise investor preferences

### Headquarters Parsing
- Fixes inconsistent entries (e.g., `Bangalore` → `Bengaluru`)
- Extracts `City`, `State`, and `Country` where possible

---

## Analysis Performed

- Top investors by number of startups funded
- Average funding per investor
- Sector preferences of investors
- Most active startup cities
- Funding trends over time

---

## Tools and Technologies

| Tool            | Purpose                    |
|------------------|----------------------------|
| Python           | Core language              |
| Pandas           | Data wrangling             |
| NumPy            | Numeric operations         |
| re (regex)       | Text parsing               |
| BeautifulSoup    | HTML parsing for scraping  |
| Matplotlib / Seaborn | Data visualization     |

---

## Future Scope
- Build an interactive dashboard using Streamlit or Dash

- Add founder information, employee count, or startup valuation

- Automate daily/weekly scraping and reporting

