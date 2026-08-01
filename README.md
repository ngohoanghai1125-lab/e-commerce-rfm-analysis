* **Data Processing & Analytics:** Python (`pandas`, `numpy`, `datetime`)
* **Data Visualization:** Python (`matplotlib`, `seaborn`), Power BI Desktop
* **Data Modeling:** Power BI Data Model (1-to-Many Relationship between Clean Sales and RFM Segments via `Customer ID`)
* **Version Control & Documentation:** Git, GitHub, Markdown

---

##  Data Cleaning & Transformation
Key preprocessing steps implemented in Python (`pandas`):
1. **Handling Missing Values:** Dropped rows where `Customer ID` or `Description` was null.
2. **Filtering Out Cancellation & Test Transactions:** 
   * Filtered out orders starting with `'C'` (Cancellations/Returns).
   * Filtered out negative or zero `Quantity` and `Price` values.
3. **Feature Engineering:**
   * Created `Total Sales = Quantity * Price`
   * Extracted `Year`, `Month`, `YearMonth`, `DayOfWeek`, `Hour` from `InvoiceDate`.

---

## RFM Customer Segmentation
Customers were evaluated based on three primary metrics calculated as of the latest transaction date in the dataset:
* **Recency (R):** Days since the last purchase.
* **Frequency (F):** Total number of distinct orders (`Invoice.nunique()`).
* **Monetary (M):** Total monetary spend (`Total Sales.sum()`).

### Scoring & Segmentation Logic
* Quantile scoring (1–5 scale) applied to R, F, and M metrics.
* Segments assigned based on RFM score patterns:
  * **Champions:** High R, High F, High M (Top buyers with recent activity).
  * **Loyal Customers:** Consistent orders over time with high monetary contribution.
  * **At Risk:** Previously active with high spending, but haven't bought recently.
  * **Hibernating:** Low recency, low frequency, low monetary value.
  * **About To Sleep, Potential Loyalist, Need Attention, Promising, New Customers, Can't Lose Them**.

---

##  Key Business Insights
1. **Strong Q4 Seasonal Surge:** Sales peak significantly in **October and November** (~$1.1M–$1.2M/month), driven by holiday shopping.
2. **Geographic Concentration:** Over **80%+ of total revenue** originates from the **United Kingdom**, followed by the Netherlands, EIRE, Germany, and France.
3. **Customer Value Distribution:** 
   * **Hibernating** represents the largest group by customer count (~1,000+ customers).
   * **Champions & Loyal Customers** generate the vast majority of cumulative revenue despite making up a smaller percentage of total users.

---

##  Power BI Interactive Dashboard
The final Power BI dashboard is structured into 3 functional zones:

1. **Executive KPI Cards:** Total Revenue (`$8.91M`), Total Orders (`18,532`), Total Customers (`4,338`).
2. **Core Trend & Breakdown Charts:**
   * **Monthly Sales Trend:** Line chart showcasing Q4 revenue acceleration.
   * **Customer Segmentation (RFM):** Horizontal bar chart mapping customer distribution across RFM groups.
   * **Top Revenue by Country:** Regional sales breakdown (UK vs International).
   * **Top 10 Selling Products:** High-performing items driving revenue.
3. **Interactive Slicers:** Date range slider (`InvoiceDate`), Country dropdown, and RFM Segment filter.

---

##  Actionable Recommendations
* **VIP Retention (Champions & Loyal Customers):** Offer exclusive preview sales, early access to holiday inventory, and dedicated loyalty perks.
* **Win-Back Campaigns (At Risk & Can't Lose Them):** Deploy personalized email offers with discount incentives to re-engage high-value inactive users before Q4.
* **Nurturing Potential Loyalists & Promising:** Introduce product recommendation engines and cross-selling bundles to increase order frequency.
* **Geographic Expansion:** Target localized marketing in top European markets (Netherlands, Germany, EIRE) to reduce over-reliance on the UK market.

---
