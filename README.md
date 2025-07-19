
# 📘 Duplicate Subscription IPO Calendar Scraper

This project is a Python tool that **scrapes IPO subscription information from `ipostock.co.kr`**, automatically collecting **subscription schedules and underwriter details** for each stock.  
It is designed to automate the process of regularly extracting the IPO calendar and saving the results to Excel.

---

## 📌 Version History

- **ver1 (2021)**  
  - Crawled IPO tables from 38 Communication's IPO calendar

- **ver2 (2022-12-14)**  
  - Changed the source to `ipostock.co.kr`  
  - Now visits each IPO’s detail page to extract underwriter information from a table

---

## 🛠️ Feature Overview

### 1. User-Defined Date Range Input
- Users input the start and end dates in `YYYY-MM-DD` format via CLI
- The specified date range is used to fetch relevant data

### 2. Collect IPO Subscription Links
- Iterates through pages on the IPO calendar at `ipostock.co.kr`
- Extracts links to individual IPO detail pages by filtering specific `<a>` tag `href` patterns

### 3. Scrape Details Per IPO
- Visits each IPO’s detail page
- Parses tables to extract: stock name, market, subscription start/end dates, and lead underwriters

### 4. Save Results
- Compiles data into a `pandas.DataFrame`
- Optionally saves the result to Excel (`.xlsx`) or CSV format

---

## 💡 Usage Example

```bash
Please enter the start date (YYYY-MM-DD) >>
2023-01-01
Please enter the end date (YYYY-MM-DD) >>
2023-12-31
```

---

## 🔗 Key Libraries Used

- `requests`, `BeautifulSoup` — for web scraping
- `pandas` — for data handling
- `datetime`, `dateutil` — for date calculations
- `time` — for throttling requests between pages

---

## 📂 Sample Output

| Stock Name | Market | Subscription Start | Subscription End | Underwriter(s)     |
|------------|--------|--------------------|------------------|---------------------|
| ABC Corp   | KOSDAQ | 2023-01-10         | 2023-01-11       | NH Investment & Securities |
| XYZ Bio    | KOSPI  | 2023-01-12         | 2023-01-13       | Mirae Asset Securities     |

---

## 🧑‍💻 Notes for Developers

- You can automate regular data collection using `crontab` or Task Scheduler
- If the website's HTML structure changes, parsing logic must be updated
- This tool can be extended to support multiple source websites in the future
