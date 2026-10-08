# Electric Utility Revenue & Billing Dashboard

# Overview
A Power BI dashboard built on synthetic utility billing data to demonstrate revenue analysis, customer billing trends, and executive-level reporting for a municipal utility operations context.

# Business Questions
- How is monthly or annual revenue trending, and which customer segments or rate classes are driving it?
- Which customers or billing periods show anomalies (such as unusually high/low bills and late payments)?
- How does billing volume and average bill amount vary by customer class, service area, or time period?
- What does a leadership-ready summary of revenue data look like at a glance?

# Data Model
Synthetic dataset covering 2,500 customers and 20,000 billing records from January 2024 through August 2026, across three tables:
- **Customers** (2,500 rows) — `CustomerID`, `CustomerClass`, `ServiceArea`, `RateType`, `StartDate`
- **Bills** (20,000 rows) — `BillID`, `CustomerID`, `BillingDate`, `Usage_kWh`, `BillAmount`, `AmountPaid`, `PaymentStatus`, `PaymentDate`, `ServiceArea`, `CustomerClass`
- **Date** — standalone calendar table for time intelligence, related to `Bills` on `BillingDate`

# Report Pages
1. **Executive Overview** — standard KPIs (Total Revenue, Total Customers, Total kWh, Average Bill, Collection Rate) alongside revenue trend by month, revenue by customer class, revenue by service area, and kWh usage by month. The Year slicer (top right) filters all visuals, because the two line charts default to showing all three years (2024-2026) of monthly data when no year is selected. The Year slicer is also available to specify individual years for the next two pages.
2. **Revenue Analysis** — Residential/Commercial/Industrial revenue and Revenue per Customer KPIs, a dual-axis Total Revenue vs. Prior Year Revenue trend line for year-over-year comparison, and revenue by service area
3. **Customer & Billing** — Average Bill, Collection Rate, Outstanding Bills, and Partial Bills KPIs, customer counts by class, a payment-status breakdown (Paid, Paid Late, Partial, Outstanding) by month, a table of the top 10% highest-billed customer classes, and a ranked table of the highest-billed individual customers

# Key DAX Measures
**Revenue**
- `Total Revenue`, `Prior Year Revenue`, `Revenue YoY %`
- `Residential Revenue`, `Commercial Revenue`, `Industrial Revenue` (by Customer Class)
- `Revenue per Customer`

**Billing & Payment Status**
- `Average Bill`, `High Bills (Top 10%)`
- `Paid Revenue`, `Outstanding Revenue`, `Partial Revenue`, `Paid Late Revenue`
- `Outstanding Bills`, `Partial Bills`
- `% Bills Fully Paid`, `Collection Rate`

**Usage & Customers**
- `Total kWh`, `Total Customers`

# Findings / Insights
- **Large Commercial customers are a disproportionate revenue driver**: They make up approximately 6.8% of the customer base (171 of 2,500 accounts) but generate 36.4% of total revenue ($3.05M of $8.38M), while Residential accounts for 78.8% of customers (1,971 accounts) but only 30.2% of revenue ($2.53M) — a typical concentration pattern worth flagging for revenue assurance focus.
- **Revenue is strongly seasonal**: Revenue peaks from roughly June-September and dropping sharply from October through December, following the trend of cooling-driven summer electricity demand.
- **Collection performance is solid but has room for improvement**: Of 20,000 bills, 1,080 (5.4%) are Outstanding and 519 (2.6%) are Partial, with another 2,382 (11.9%) Paid Late — a 93.68% collection rate overall, but nearly 1 in 5 bills involves some payment friction.
- **Eastside and Westside are the top-revenue service areas**: They are about $1.5M+ each, while Downtown and Rural trail furthest behind, which could inform where to prioritize revenue-assurance or outreach efforts.

# Technologies Used
- Power BI Desktop (data modeling, DAX, report design)
- Synthetic data generation (retrieved from https://www.imagine.art/imagine-computer/ai-spreadsheet-generator)

# Disclaimer
Data is synthetic and generated for portfolio/demo purposes. It does not represent any real utility's actual billing data.
