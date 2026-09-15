 FMCG-Inventory-Control-Tower
An enterprise-grade, automated **Inventory Control Tower** built in Excel to optimize working capital, balance safety stock against demand volatility, and generate real-time purchase order signals across **50 FMCG SKUs** (modeled after leading FMCG product categories including Parachute, Saffola, and Livon).

---

 📌 Executive Summary

Maintaining optimal stock levels in the Fast-Moving Consumer Goods (FMCG) sector requires balancing two competing financial pressures:
* **Carrying Costs:** Excess stock ties up working capital and increases warehouse holding costs.
* **Stockout Risks:** Under-stocking leads to lost revenue, shelf-out-of-stock penalties, and reduced customer loyalty.

This model automates decision-making by integrating **Economic Order Quantity (EOQ)** batch sizing with **Statistical Safety Stock** and **Reorder Point (ROP)** mechanics, taking into account vendor Lead Times and Minimum Order Quantities (MOQ).

---

## 🛠️ Key Supply Chain Concepts & Formulas

### 1. Economic Order Quantity (EOQ)
Calculates the optimal order batch size ($Q^*$) that minimizes the sum of annual ordering and holding costs:

$$\text{EOQ} = \sqrt{\frac{2 \cdot D \cdot S}{H}}$$

* $D$ = Projected Annual Demand (Units)
* $S$ = Fixed Procurement/Order Cost ($\text{INR}$)
* $H$ = Annual Unit Holding Cost ($H = \text{Unit Purchase Cost} \times \text{Holding Rate}$)

### 2. Statistical Safety Stock ($SS$)
Maintains a dynamic inventory buffer to protect against daily demand fluctuations ($\sigma_d$) while targeting specific customer service levels ($90\% - 98\%$):

$$SS = \text{ROUNDUP}\left(Z \times \sigma_d \times \sqrt{L}, 0\right)$$

* $Z$ = Statistical Z-Score corresponding to Target Service Level (`=NORM.S.INV(Service_Level)`)
* $\sigma_d$ = Standard Deviation of Daily Sales
* $L$ = Supplier Base Lead Time (Days)

### 3. Reorder Point (ROP) & Purchase Triggers
Triggers a replenishment signal as soon as net available stock drops to or below lead-time demand plus safety stock:

$$\text{ROP} = (d \times L) + SS$$

$$\text{Order Action} = \text{IF}\left(\text{Available Stock} \le \text{ROP}, \max(\text{EOQ}, \text{MOQ}), 0\right)$$



 📊 Dashboard & Control Tower Features

* Executive KPI Summary Cards:** Instant visibility into **SKUs Needing Reorder**, **Total Safety Stock Buffer Units**, and **Total Working Capital Committed (EOQ Purchase Value)** using `COUNTIF`, `SUM`, and `SUMPRODUCT` logic.
* In-Cell Visualization Engine:** Applied Gradient Data Bars to track buffer levels and traffic-light Conditional Formatting (`Icon Sets`) to highlight SKUs entering critical stock zones.
  * Portfolio Analytics Charts:** 
  * Donut Chart:** *Inventory Health Breakdown* (Sufficient Stock vs. Reorder Required).
  * Clustered Column Chart:** *Top 15 SKUs: Batch Order Size (EOQ) vs. Buffer Stock*.

  💻 Technical Excel Skills Demonstrated

  * Statistical & Logical Functions:** `NORM.S.INV`, `SQRT`, `ROUNDUP`, `COUNTIF`, `SUMPRODUCT`, nested `IF`, `CONCATENATE`.
  * Dynamic Data Visualization:** Conditional Formatting (Data Bars & Icon Sets), Doughnut Charts, Clustered Column Charts.
  * Dashboard Design:** Gridless Executive Layout, KPI Summary Blocks, Center-Across-Selection formatting architecture.

