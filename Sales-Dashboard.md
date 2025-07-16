Below is a streamlined, step-by-step tutorial to build the Sales Dashboard in Power BI Desktop, based on the lab instructions in your PDF. Citations reference the original lab document for each major phase.

---

## Prerequisites

* Install **Power BI Desktop** (latest version).
* Download the three data files into a local folder:

  * `SalesDashboard-CustomerMD.csv`
  * `SalesDashboard-ProductMD.csv`
  * `SalesDashboard-Transactions.xlsx`

---

### 1. Load Customer Master Data

1. In Power BI Desktop, click **Get Data → Text/CSV**.
2. Browse to `SalesDashboard-CustomerMD.csv` and click **Open**.
3. In the preview dialog, verify the delimiter and header row are correct, then click **Load**.&#x20;

---

### 2. Load & Transform Product Master Data

1. Click **Get Data → Text/CSV**, select `SalesDashboard-ProductMD.csv`, then **Transform Data** instead of Load.
2. In Power Query Editor, on the **Home** ribbon click **Use First Row as Headers** to promote row 1 to column names.
3. Click **Close & Apply** to load the cleaned table into the model.&#x20;

---

### 3. Load & Shape Transactions Data

1. Click **Get Data → Excel**, select `SalesDashboard-Transactions.xlsx`, check **Transactions**, then **Transform Data**.
2. **Convert Invoice\_time**

   * In Power Query, click the data-type icon next to **Invoice\_time** → **Date/Time**.
3. **Add Sales column**

   * On the **Add Column** ribbon, choose **Custom Column**.
   * Name it **Sales**, and enter the formula

     ```
     [Quantity] * [Price]
     ```
   * Click **OK**, then set its data type to **Decimal Number**.
4. Click **Close & Apply** to commit the query.&#x20;

---

### 4. Verify & Edit Table Relationships

1. Switch to **Model View** (third icon at left).
2. Confirm Power BI auto-created:

   * **Transactions\[StockCode] → ProductMD\[StockCode]** (Many-to-One)
   * **Transactions\[Customer\_ID] → CustomerMD\[Customer\_ID]** (Many-to-One)
3. If needed, double-click a relationship line to adjust columns or cardinality.&#x20;

---

### 5. Build the **Sales Overview** Page

1. **Bar Chart** – Sales by Category

   * In **Report View**, click **Stacked Bar Chart** icon.
   * From the **Fields** pane drag **ProductMD\[Category]** → **Axis**, and **Transactions\[Sales]** → **Values**.&#x20;

2. **Treemap** – Category & Subcategory Share

   * Click **Treemap** icon.
   * Drag **Category** → **Group**, **Subcategory** → **Details**, **Sales** → **Values**.

3. **Line Chart** – Sales Over Time

   * Click **Line Chart**.
   * Drag **Invoice\_time** → **Axis**, **Sales** → **Values**.
   * Use the “Drill down” arrows at top-right of the visual to expand from Year → Quarter → Month.

4. **Map** – Sales by Country

   * Select **Map** visual.
   * Drag **CustomerMD\[Country]** → **Location**, **Sales** → **Size**.

5. **Time Slicer**

   * Add **Slicer** visual.
   * Drag **Invoice\_time** → **Field**.

6. **Domestic vs. International Slicer**

   * Return to **Transform Data** → select **CustomerMD**.
   * On **Add Column** ribbon choose **Conditional Column**.

     * Name it **Type**.
     * If **Country** = `United Kingdom` then `"Domestic"`, else `"International"`.
   * **Close & Apply**.
   * Add a second **Slicer** with **CustomerMD\[Type]**.&#x20;

7. **Page Title**

   * On **Insert** ribbon click **Text box**, type **Sales Overview**, and format as desired.

8. **Adjust Interactions**

   * With any visual selected, go to **Format → Edit interactions**.
   * Click the antecedent chart, then on each dependent visual choose **Filter** (funnel icon) to enforce filtering rather than mere highlighting.&#x20;

---

### 6. Build the **Sales Details** Page

1. Add a new page via the **+** at bottom. Rename it **Sales Details**.

2. **Matrix** – Quarterly Sales by Category/Subcategory

   * Choose **Matrix** visual.
   * Drag **Category** then **Subcategory** → **Rows**; **Invoice\_time** → **Columns**; **Sales** → **Values**.
   * Drill down rows and columns to show sub-levels.
   * In **Format** pane turn off **Column subtotals** and set **Value decimal places** to 0.&#x20;

3. **Donut** – Domestic vs. International

   * Insert **Donut** visual.
   * Drag **Type** → **Legend**, **Sales** → **Values**.

4. **Country Table**

   * Add **Table** visual.
   * Drag **Country** then **Sales** into it; click **Sales** header to sort descending.

5. **Top Articles Table**

   * Add another **Table**.
   * Drag **Description**, **Quantity**, **Sales** (in that order).
   * Sort by **Sales** descending and set **Value decimal places** to 0.

6. **Page Title**

   * Insert **Text box**, type **Sales Details**, and match formatting from the first page.&#x20;

---

### 7. Publish & Refresh

1. Click **Home → Publish**, sign in, and choose your workspace.
2. On the Power BI Service, use **Refresh** (or schedule via gateway) to keep data up to date.&#x20;

---

You now have a two-page interactive dashboard that lets users explore overall sales trends and drill into detailed views by category, time, country, and product—fully built from raw CSV/Excel sources using Power BI’s ETL, modeling, and visualization features.
