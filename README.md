# Executive Sales Performance Dashboard — Documentation

## 1. Business Problem Summary
The enterprise retail ecosystem faces significant challenges in optimizing overall bottom-line margin expansion despite maintaining healthy top-line sales growth. Operational and financial inefficiencies are introduced through macro seasonality, non-uniform regional performance, undisciplined discounting policies, and friction in post-sale logistics (such as high-density product return zones). 

This project delivers a centralized data visualization solution built in Tableau. It provides leadership with the tools necessary to diagnose structural margin erosion, monitor geographic demand patterns, evaluate sub-category profitability, and transition from descriptive oversight to proactive operational strategy.



## 2. Dataset Description
The underlying analytical engine relies on a multi-dimensional retail transactional dataset that captures end-to-end purchasing and delivery lifecycles.
*   **Temporal Fields:** `Order Date`, `Ship Date` (used to evaluate seasonal cyclicality and operational fulfillment timelines).
*   **Geographic Dimensions:** `Region`, `State`, and localized markets across administrative zones.
*   **Product Hierarchy:** Market classifications segmented into `Category` and item-specific `Sub-Category`.
*   **Customer Segmentation:** Tracks procurement behavior across `Consumer`, `Corporate`, and `Home Office` profiles.
*   **Financial Metrics:** Transactional tracking of gross `Sales` volume, explicit item-level `Profit`, and applied `Discount` rates.
*   **Fulfillment Logs:** Binary tracking flags documenting operational supply chain performance and post-sale `Return Flag` indicators.



## 3. Tableau Workbook Description
The workbook is developed using **Tableau Desktop Public Edition** (`executive_dashboard.twbx`). It transitions from granular worksheets into a unified executive-facing dashboard platform. 

The architecture leverages unified schema relationships across primary operational parameters, allowing data points to connect contextually. Rather than serving as isolated graphs, the workbook is built as an interactive application where user actions on geographic charts or category filters instantly slice backend datasets across the entire visual layout.



## 4. Calculated Fields Created
To extract deeper business intelligence beyond raw transactional variables, the following calculated fields were developed within the data model:

*   **Profit Margin (%)**
    *   *Formula:* `SUM([Profit]) / SUM([Sales])`
    *   *Purpose:* Establishes a standardized efficiency metric to evaluate relative profitability across segments and categories independent of their absolute sales volumes.
*   **Return Rate Ratio**
    *   *Formula:* `COUNT(IF [Return Flag] = 1 THEN [Order ID] END) / COUNT([Order ID])`
    *   *Purpose:* Quantifies post-sale customer friction and warehouse fulfillment errors across different macro distribution networks.
*   **Shipping Days / SLA Variance**
    *   *Formula:* `DATEDIFF('day', [Order Date], [Ship Date])`
    *   *Purpose:* Tracks logistics performance against target delivery service level agreements (SLAs).



## 5. Dashboard Components
The main interface dashboard (`Dashboard 1`) unifies several major visual components into a balanced grid layout optimized for executive review:
1.  **Macro Executive KPI Cards:** High-contrast callout metrics presenting global aggregations for *Total Sales*, *Total Profit*, and *Relative Profit Margin* at a single glance.
2.  **Sales Trend View (`sales_trend_view`):** A continuous timeline charting revenue velocity over months and years to reveal multi-year trajectory shifts and predictable performance peaks.
3.  **Geographic Density Map (`sales_by_state`):** A filled map visualization providing spatial orientation of top-line revenue concentrations across localized administrative boundaries.
4.  **Sub-Category Profitability Rankings:** A sorted horizontal bar chart identifying high-performing product lines relative to margin-draining commodity items.
5.  **Customer Segment Performance:** A column chart breaking out purchasing distributions across corporate and home office clients.
6.  **Regional Return Analysis (`Return analysis view`):** A stacked bar breakdown isolating regional operational bottlenecks and product return volumes.
7.  **Profitability vs. Discount Distribution:** A detailed scatter plot tracking transaction density against discount percentages to highlight margin erosion thresholds.


## 6. Filters and Interactions Used
The dashboard is built with dynamic interactions to support deep-dive diagnostic filtering:
*   **Global Dimension Dropdowns:** Global filter cards (e.g., `Region`, `Category`, `Customer Segment`) configured via the **"Apply to Worksheets > All Using This Data Source"** command to slice all charts simultaneously.
*   **Map Action Filtering ("Use as Filter"):** The `sales_by_state` map chart acts as an interactive filter. Clicking a localized state automatically isolates data for that territory across the timeline, KPIs, and scatter plots.
*   **Hover Tooltips & Highlights:** Context-aware informational overlays provide precise data callouts upon mouse-hover without cluttering the screen layout.



## 7. Key Business Insights
*   **Mid-Year Sales Cyclicality:** The enterprise experiences regular mid-year demand peaks followed by immediate post-quarter corrections, requiring proactive supply chain stocking patterns.
*   **High-Margin Anchors:** Tech sub-categories like **Copiers and Phones** generate our strongest absolute profit margins, whereas commodity furniture lines like **Tables** act as net-negative margin drags.
*   **Discount Erosion Thresholds:** Transaction profitability remains stable under 10% discounts but degrades rapidly past the 20% mark, indicating a need for strict pricing guardrails.
*   **Regional Returns Friction:** The **West Region** exhibits disproportionately high return flags and SLA variances, indicating localized logistics or warehouse fulfillment issues.



## 8. Dashboard Story Summary
The dashboard tells a continuous strategic story for executive leadership:
1.  **The Core Growth Engine:** B2B revenue is healthy, driven by corporate procurement accounts buying high-margin technology equipment during predictable seasonal spikes.
2.  **The Profit Leak:** Top-line growth is actively undermined by undisciplined discretionary discounting on commodity office goods, which shifts stable baseline categories into net-losses.
3.  **Logistical Friction:** Post-sale operational challenges in the West region create delivery gaps and return spikes that erode the financial gains achieved by our high-performing central territories.
4.  **The Path Forward:** Implementing discount guardrails, optimization of regional logistics hubs, and launching tailored product bundles for the expanding Home Office segment provide paths to expand overall enterprise margins.



## 9. Assumptions and Limitations
*   **Static Cost Metrics:** Profit fields are evaluated as a final static variable; the current dashboard cannot break down underlying operational dynamics like fluctuating vendor costs, marketing acquisition fees, or real-time freight surcharges.
*   **Dimensional Filtering Mismatches:** Specialized charts built around hyper-specific dimensions can experience broken interactions if cross-source data relationships are not fully unified at the database level.
*   **Data Completeness:** Analysis assumes all order transaction entries, return logs, and delivery dates are logged uniformly with zero administrative lag across all distribution centers.



## 10. Screenshots Included
The documentation framework includes two primary view captures to verify design integrity and dynamic functionality:
1.  **`executive_dashboard_default.png`**: Captures the global baseline state of the dashboard, showing macro-level performance numbers and standard categorical balances across the entire layout.
2.  **`filter_interaction_view.png`**: Demonstrates the dashboard's interactive filtering capabilities in action. This screenshot shows the layout dynamically updating—with adjusted KPIs, map highlights, and filtered scatter plots—when a single state territory (such as Madhya Pradesh) is isolated.