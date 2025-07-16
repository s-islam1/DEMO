Here’s what this lab is all about and exactly how to complete it:

**What we’re doing here**
We’re using Power BI Desktop to add new fields—called **calculated columns**—to an imported data model by writing simple DAX formulas. Calculated columns let you combine or transform existing columns in ways that the original data didn’t provide. In this lab you’ll:

* **Part 1:** Create a `ProductFullCategory` column that concatenates category and subcategory names into one field.
* **Part 2:** Create an `Active StoreName` column that uses `IF` logic to label each store either by name (if active) or as “Inactive.”&#x20;

---

## Prerequisites

1. Download and extract the **Contoso Sales Sample** PBIX file from the Lab 9 folder.
2. Open **Power BI Desktop** and load that PBIX.

---

## Part 1 – Combine Category & Subcategory into `ProductFullCategory`

1. **Locate the table**
   In the **Fields** pane, find **ProductSubcategory**.
2. **Add a new column**
   Right-click **ProductSubcategory** (or click the ellipsis …) and choose **New column**.&#x20;
3. **Rename & start your formula**
   In the formula bar, rename the default `Column` to:

   ```
   ProductFullCategory =
   ```
4. **Pull in the related category**
   After the equals sign, type `RELATED(`, select `RELATED`, then choose the `[ProductCategory]` column from the **ProductCategory** table, and close the parenthesis:

   ```DAX
   ProductFullCategory = RELATED( ProductCategory[ProductCategory] )
   ```
5. **Concatenate with subcategory**
   Append:

   ```DAX
     & " - " & [ProductSubcategory]
   ```

   So the full expression reads:

   ```DAX
   ProductFullCategory =
     RELATED( ProductCategory[ProductCategory] )
     & " - "
     & [ProductSubcategory]
   ```
6. **Validate**
   Press **Enter** (or click the checkmark). If there are no errors, you’ll see `ProductFullCategory` appear under **ProductSubcategory** with the calculated-column icon.&#x20;
7. **Use in a report**

   * Drag **ProductFullCategory** onto the canvas to create a table.
   * Then drag **SalesAmount** from the **Sales** table into that table to see sales by your new full-category field.

---

## Part 2 – Label Active vs. Inactive Stores in `Active StoreName`

1. **Locate the table**
   In the **Fields** pane, find **Stores**.
2. **Add a new column**
   Right-click **Stores** (or click …) and choose **New column**.&#x20;
3. **Rename & begin `IF`**
   In the formula bar, rename `Column` to:

   ```
   Active StoreName =
   ```

   Then type `IF(` and select the `IF` function from the suggestions.
4. **Define the logical test**
   Inside the parentheses, set the test to `[Status] = "On"`, then type a comma.
5. **True result**
   After the comma, insert `[StoreName]`, then another comma. This covers the “if true” case.
6. **False result**
   Type `"Inactive"`, then close the parenthesis.
7. **Final formula**

   ```DAX
   Active StoreName =
     IF(
       [Status] = "On",
       [StoreName],
       "Inactive"
     )
   ```
8. **Validate**
   Press **Enter** (or click the checkmark). You’ll now see `Active StoreName` in the **Stores** table.&#x20;
9. **Use in a report**

   * Drag **Active StoreName** onto the canvas to build a table.
   * Add **SalesAmount** to see active stores by name, with all inactive ones grouped under “Inactive.”

---

### Summary

You’ve now created two calculated columns that enrich your model:

* **ProductFullCategory** – combines related table fields via `RELATED` and string concatenation.
* **Active StoreName** – uses `IF` logic to branch values based on store status.

These steps illustrate the power of DAX for on-the-fly data modeling in Power BI Desktop. Once comfortable with these basics, you can explore many more DAX functions to tailor your data even further.
