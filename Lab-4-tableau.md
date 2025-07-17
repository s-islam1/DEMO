Below is a clear, step‑by‑step guide to completing the “Common Charts” lab in Tableau, based on your provided starter workbook **Tableau Fundamentals – Common Charts\_starter**.

---

## 1. Bar Chart

*Question #1: Which hurricane has the highest barometric pressure? Does pressure go up or down as category increases?*

1. **Create and rename sheet**

   * Click the “New Worksheet” button.
   * Double‑click its tab name and enter **Bar Chart**.&#x20;

2. **Build the basic bar chart**

   * From the **Dimensions** pane, drag **Category** to **Columns**.
   * From the **Measures** pane, drag **Pressure** to **Rows**.&#x20;

3. **Aggregate to average**

   * Right‑click the **Pressure** pill on **Rows** → **Measure** → **Average**.&#x20;

4. **Sort descending**

   * Hover over the vertical axis until the sort icon appears.
   * Click it and choose **Sort Descending**.&#x20;

5. **Flip orientation**

   * Drag **Category** from **Columns** to **Rows**, and **Pressure** from **Rows** to **Columns**.&#x20;

6. **Color by a measure vs. dimension**

   * Drag **Storm Speed** (measure) to the **Color** mark: you’ll get a gradient.
   * Remove **Storm Speed** and drag **Date/Time** (dimension) to **Color**: you’ll get distinct colors per date.&#x20;

7. **Experiment with additional fields**

   * Try dragging other measures/dimensions (e.g. Hurricane ID, Wind Speed) onto **Size**, **Label**, **Detail**, etc., to see how the chart’s story changes.&#x20;

---

## 2. Line Graph

*Question #2: Have hurricanes become stronger (by wind speed) over time?*

1. **Create and rename sheet**

   * New worksheet → double‑click tab → **Line Graph**.&#x20;

2. **Plot date vs. wind speed**

   * Drag **Date/Time** to **Columns**.
   * Drag **Wind Speed** to **Rows**.&#x20;

3. **Change to average**

   * Right‑click **Wind Speed** on **Rows** → **Measure** → **Average**.&#x20;

4. **Add a second measure (Storm Speed)**

   * Drag **Storm Speed** to **Rows**.
   * Change its aggregation to **Average** (right‑click → **Measure** → **Average**).&#x20;

5. **Create a dual‑axis**

   * Drag the **Storm Speed** pill from its own axis onto the right side of the **Wind Speed** chart until you see the green single‑bar icon → release.&#x20;

6. **Change mark type for Storm Speed**

   * On the **Marks** card, click **AVG(Storm Speed(mph))** → from the drop‑down, select **Bar**.&#x20;

> *Tip:* If you wanted a combined axis instead of dual, drag **Storm Speed** onto the left axis until the double‑bar icon appears.

---

## 3. Scatter Plot

*Question #3: As hurricanes strengthen (wind speed ↑, pressure ↓), how does forward movement (storm speed) relate?*

1. **Create and rename sheet**

   * New worksheet → **Scatter Plot**.&#x20;

2. **Plot pressure vs. wind speed**

   * Drag **Pressure** to **Columns**, **Wind Speed** to **Rows**.&#x20;

3. **Filter to category 0**

   * Drag **Category** onto the **Filters** card → select only **0**.&#x20;

4. **Change both to averages**

   * Right‑click each axis measure → **Measure** → **Average**.

5. **Add detail**

   * Drag **Hurricane ID** to **Detail** on the **Marks** card (so each point is one storm).&#x20;

6. **Fix axis range**

   * Double‑click the **Avg. Pressure** axis title → select **Fixed** → set **Start = 975**, **End = 1030** → click **OK**.&#x20;

> Hovering over each dot now shows its pressure, wind speed, and ID.

---

## 4. Map

*Question #4: Where do hurricanes originate, and do those nearer land move slower?*

1. **Create and rename sheet**

   * New worksheet → **Maps**.&#x20;

2. **Plot geographic points**

   * Double‑click **Latitude** and **Longitude** in **Measures** → Tableau auto‑creates a point map.
   * Drag **Hurricane ID** to **Detail** so each point is one storm.&#x20;

3. **Color by wind speed**

   * Drag **Wind Speed** to **Color** on the **Marks** card → right‑click it → **Measure** → **Average**.&#x20;

4. **Adjust opacity**

   * Click the **Color** mark → set **Opacity** to **80%** (so overlapping points remain visible).&#x20;

> Darker points indicate higher average wind speeds. Notice geographic patterns (e.g., offshore vs. near‐shore storms).

---

### Next Steps / Reflection

* Answer the lab’s discussion questions in your worksheet (e.g., which category shows highest pressure, trends over time).
* Try adding **Trend Lines** (Analytics pane → **Trend Line**) to the line graph for additional insight.
* Explore the “Additional Reading/Resources” links for deeper practice .
