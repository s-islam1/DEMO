**Step‑by‑Step Tutorial: Creating and Using Measures in Power BI Desktop**
*(Based on “010 Creating Measures.pptx”) *

---

## 1. Prepare Your Environment

1. **Download the sample file**

   * Locate the “Contoso Sales Sample for Power BI Desktop.pbix” in your Lab 8 folder.
   * Copy it to a folder on your computer where you can easily find it.&#x20;
2. **Launch Power BI Desktop**

   * If you haven’t installed it, download and install from Microsoft.
   * Open Power BI Desktop.

---

## 2. Explore Automatic Measures

1. **Open the sample report**

   * In Power BI Desktop, go to **File > Open**, browse to your Contoso.pbix file, and click **Open**.&#x20;
2. **View a default aggregation**

   * In the **Fields** pane, expand **Sales**.
   * Either check the box next to **SalesAmount** or drag **SalesAmount** onto the blank report canvas.
   * A column chart appears showing the **Sum** of all SalesAmount values.
3. **Change the aggregation type**

   * Click the chart to select it.
   * In the **Visualizations** pane under **Values**, click the down-arrow next to **SalesAmount**.
   * Choose **Average**. The chart now shows the average sales amount.&#x20;

---

## 3. Understand Context

* **Context** means the way Power BI filters and groups data for your visuals.
* Try dragging **RegionCountryName** (from the **Geography** table) onto your SalesAmount chart. Notice how the measure recalculates per country.&#x20;

---

## 4. Create a Custom Measure (“Net Sales”)

1. **Initiate a new measure**

   * In the **Fields** pane, right‑click the **Sales** table (or click “…”), then choose **New measure**.
   * Alternatively, on the Home ribbon, under **Calculations**, click **New measure** (be sure **Sales** is selected first).&#x20;
2. **Rename and start the formula**

   * In the formula bar, replace the default name **Measure** with **Net Sales**.
   * Type an equals sign (`=`) to begin your DAX formula.
3. **Add the first SUM expression**

   * Type `SUM(` and select **Sales\[SalesAmount]** from the suggestions.
   * Close the parenthesis: `SUM(Sales[SalesAmount])`.&#x20;
4. **Subtract discounts and returns**

   * After the first `)`, type ` - SUM(`.
   * Select **Sales\[DiscountAmount]**, close `)`, then type ` - SUM(` again.
   * Select **Sales\[ReturnAmount]** and close the final `)`.
   * Your full formula should read:

     ```
     Net Sales =
       SUM(Sales[SalesAmount])
       - SUM(Sales[DiscountAmount])
       - SUM(Sales[ReturnAmount])
     ```
5. **Commit the measure**

   * Press **Enter** or click the checkmark to validate.

---

## 5. Use Your “Net Sales” Measure

1. **Add Net Sales to a visual**

   * Drag **Net Sales** from **Sales** onto the report canvas.
2. **Compare to Total Sales**

   * Also drag **SalesAmount** onto the same chart.
   * Drag **RegionCountryName** onto **Axis** (or Legend) to see side‑by‑side totals per region.&#x20;

---

## 6. Create and Configure a Year Slicer

1. **Insert a blank table (for slicer base)**

   * Click a blank area of the canvas.
   * In **Visualizations**, select the **Table** icon.
2. **Show individual years**

   * Drag **Year** from the **Calendar** table into the **Values** field.
   * In **Values**, click the down‑arrow by **Year** and choose **Don’t summarize**.
3. **Convert to slicer**

   * With the table selected, click the **Slicer** icon.
   * If it appears as a slider, click its down‑arrow and choose **List**.
4. **Filter your chart**

   * Click any year in the slicer to filter both the **SalesAmount** and **Net Sales** charts.&#x20;

---

## 7. Build a Second Measure (“Net Sales per Unit”)

1. **Create a new measure** in the **Sales** table: right‑click **Sales** > **New measure**.
2. **Name it** `Net Sales per Unit =`.
3. **Reference your Net Sales measure**

   * Type `[` and select **Net Sales** from the suggestions.
4. **Divide by quantity sold**

   * After `]`, type ` / SUM(`, select **Sales\[SalesQuantity]**, and close `)`.
   * Final DAX:

     ```
     Net Sales per Unit =
       [Net Sales] / SUM(Sales[SalesQuantity])
     ```
5. **Commit** the formula.&#x20;

---

## 8. Visualize “Net Sales per Unit” with a Treemap

1. **Add the measure**

   * Drag **Net Sales per Unit** onto the canvas.
2. **Change visualization**

   * In **Visualizations**, select **Treemap**.
3. **Group by product**

   * Drag **ProductCategory** (or **ProductName**) onto the **Group** area.
4. **Experiment**

   * Try different fields (e.g. Region, Year) to see context‑driven recalculations.&#x20;

---

## 9. Tips for Working with DAX

* **Expanding the formula bar**: Click the down‑arrow at the right of the formula bar to get more editing space.
* **Multi‑line formulas**: Use **Alt + Enter** to insert line breaks and **Tab** for indentation.
* **Quick measures**: For common tasks, right‑click a table in **Fields** > **New quick measure**, then follow the dialog prompts.&#x20;

---

### You’re Done!

You’ve learned how to:

* View and modify automatic measures
* Create model measures with DAX
* Leverage context via slicers
* Build and format custom visuals like treemaps

Explore further with Microsoft’s DAX references and quick‑measure guides.
