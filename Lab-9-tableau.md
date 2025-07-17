**Part 1: Build the Superstore Sales KPI Dashboard**

1. **Open the starter workbook**

   * Launch Tableau Desktop and open **Tableau Fundamentals – Combining Views\_starter**.&#x20;
2. **Create a new dashboard**

   * Click the **New Dashboard** icon (bottom of the workspace).
   * Double‑click its tab and rename it **Superstore Sales KPI**.&#x20;
3. **Set up device layout**

   * On the top menu, go to **Dashboard ▶ Device Layouts** and choose **Desktop**.&#x20;
4. **Format background**

   * With the dashboard selected, click **Format** on the Dashboard menu.
   * In the Format pane, under **Shading**, set **Dashboard** background to **Light Gray**, then close the pane.&#x20;
5. **Add the key views**

   * From the **Sheets** list, drag **Total Sales per Salesperson** onto the upper half of the canvas.
   * Drag **Sales by Shipping Mode** into the lower left—drop when you see a gray box filling half the width.
   * Drag **Sales per Year** into the lower right half.&#x20;
6. **Insert a title text object**

   * From the **Objects** pane, drag **Text** to the top‑left corner until it covers about one‑third of the width.
   * In the editor, type **Superstore Sales**, set the font size to **22 pt**, and click **OK**.&#x20;
7. **Swap sheets if needed**

   * Click the **Sales by Shipping Mode** container, hover in the Dashboard pane over **Top Sales by State**, and click the curved double‑arrow to swap without disturbing layout.&#x20;

---

**Part 2: Add Interactivity with Dashboard Actions**

1. **Turn a view into a filter**

   * In the dashboard, click the drop‑down arrow on **Sales per Year**.
   * Select **Use as Filter**.&#x20;
2. **Verify filter action**

   * Click any mark in **Sales per Year** (e.g., **Technology**). Watch the other charts update to show, for instance, the top three states for that category.&#x20;
3. *(Optional)* Configure via **Dashboard ▶ Actions** for more control over source/target sheets, clearing behavior, or adding highlight/navigation actions.&#x20;

---

**Part 3: Create a Tableau Story**

1. **Start a new story**

   * Click **New Story** (bottom tab bar) and rename it **Superstore Sales Story**.&#x20;
2. **Build Story Point 1**

   * Drag **Total Sales per Salesperson** onto the story canvas.
   * Click the caption box beneath it and enter:

     > *3/4 people have sold over 500,000 in products.*&#x20;
3. **Build Story Point 2**

   * Drag **Sales per Year** to the next point.
   * Edit its caption to:

     > *Sales for each category have increased over the years.*&#x20;
4. **Build Story Point 3**

   * Drag **Top Sales by State** onto the third point.
   * Change the caption to:

     > *The lowest amount of sales occurred in Virginia and Michigan.*&#x20;
5. **Annotate key insights**

   * On each story point, click **Annotate** (on the toolbar) to add callouts or highlight marks that reinforce your narrative.&#x20;

---

*You have now combined multiple views into a single dashboard, added interactive filtering, and crafted a data story using Tableau’s Story feature.*
