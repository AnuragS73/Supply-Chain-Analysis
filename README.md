# Supply Chain Delivery Delay Analysis

## 1. Business Problem
A large portion of orders are being delivered later than their scheduled shipment date, impacting customer experience and profitability. The business needs visibility into how widespread delays are, which segments (shipping mode, product category, region, time period) are most affected, and how delays correlate with profit so corrective action can be prioritized.

## 2. Objective
Perform exploratory data analysis on the DataCo Supply Chain dataset to:
- Quantify the scale of delivery delays and on-time performance.
- Identify the operational dimensions (shipping mode, product category, region, customer segment, order type) that drive delays.
- Analyze the relationship between delivery delays and order profitability.
- Detect time-based patterns (day of week, month, hour) in delay rates to support seasonal/operational planning.

## 3. Methods
- **Data Cleaning**: Standardized column names; removed irrelevant/PII columns (customer details, product descriptions, IDs, location coordinates, etc.); filtered out cancelled shipments; converted order and shipping dates to datetime.
- **Feature Engineering**: Derived `order_processing_time`, `delay` (actual vs. scheduled shipment days), `is_delayed` flag, `profit_tag` (Profit/Loss/Break Even), and time-based features (`order_day`, `order_month`, `order_hour`).
- **Exploratory & Statistical Analysis**: Distribution analysis of delays and profit (pie charts, bar plots); grouped aggregations by category, shipping mode, region, department, and order type to compute delay percentages.
- **Root Cause Analysis**: Region-level breakdown of top delay drivers across shipping mode, customer segment, department, order status, and order type.
- **Time Series Analysis**: Delay percentage trends by weekday, month, and hour to identify temporal patterns.

## 4. KPIs Used
- Total Orders
- Delayed Orders & On-Time Delivery count
- On-Time Delivery %
- Late Delivery %
- 90th Percentile Delay Days (days within which 90% of delayed orders are delivered)
- Total Profit (from profitable orders)
- Total Loss Due to Delay (profit/loss on delayed orders)
- Delay % by category, shipping mode, region, department, order type
- Delay % by weekday, month, and hour

## 5. Outcome

**Delay & Profit Patterns**
- 1-day delayed deliveries represent the largest share of orders (~31%) and also generate the highest total profit (~1.2M), followed by on-time deliveries (~815K).
- Average profit per order is highest for shipments delivered 2 days early, while both total and average profit decline as delays exceed 1 day, with 3–4 day delays being the least profitable.

**Key Delay Drivers**
- Shipping mode is the primary driver of delays — First Class and Second Class shipments show significantly higher delay rates than Standard Class.
- Certain product categories (Golf Bags & Carts, Lacrosse, Cameras) show consistently higher delay rates, pointing to inventory/supplier issues.
- Customer segment, payment type, region, and department show minimal variation and are not major delay drivers.

**Time-Based Patterns**
- Delay rates are nearly constant across weekdays (~54–55.5%), indicating delays stem from systemic operational issues rather than weekday demand fluctuations.
- Delay rates vary moderately by month (~53.7%–55.4%), peaking in August, September, and December (seasonal/peak demand effect) and lowest in July.

**Business Recommendations**
- Investigate expedited shipping (First/Second Class) fulfillment and carrier processes to address the largest delay contributor.
- Review inventory availability, supplier lead times, and replenishment planning for high-delay product categories.
- Implement seasonal capacity planning for peak months (Aug, Sep, Dec) to mitigate forecast demand spikes.
- Prioritize fixes to overall operational processes over weekday-specific interventions, since delay rates are uniform across the week.
