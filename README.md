# Part 1: Business Data Cleaning, Validation & Excel Reporting

## Problem Summary

The retail company exported order-level sales data from multiple internal systems. The raw dataset contained multiple data quality issues, including inconsistent text formatting, duplicate records, missing values, invalid discounts, date inconsistencies, and calculation mismatches.
The objective of this project was to clean and validate the dataset, apply business rules, generate calculated columns, and create summary reports for business analysis and decision making.
---

## Dataset Description

The dataset contains order-level transaction data with the following fields:
- Order ID
- Customer Name
- Customer Segment
- Region
- State
- City
- Category
- Sub-Category
- Order Date
- Ship Date
- Ship Mode
- Quantity
- Unit Price
- Sales
- Cost
- Profit
- Discount
- Payment Status
- Order Status

The original dataset was preserved and all cleaning activities were performed on a separate file.

---

## Tools Used

- Microsoft Excel
- Pivot Tables
- Conditional Formatting
- Find and Replace 
- Flash Fill
- Excel Functions:
    - TRIM ()
    - SUBSTITUTE ()
    - IF ()
    - YEAR ()
    - MONTH ()
    - DATEDIF ()

---

## Cleaning Steps Performed
### 1. Raw Data Preservation

Original dataset stored as:

`data/raw_orders.xlsx`

Cleaned dataset created as:

`data/cleaned_orders.xlsx`

### 2. Text Cleaning

Standardized:

- customer_name
- segment
- region
- state
- city
- category
- sub_category
- ship_mode
- payment_status
- order_status

Actions performed:

- Removed leading/trailing spaces
- Removed extra spaces
- Standardized capitalization
- Removed unwanted characters

### 3. Date Cleaning

Validated:

- Missing dates
- Invalid dates
- Text values not recognized as dates
- Ship dates earlier than order dates

Created:

- shipping_delay_days

### 4. Duplicate Handling

Identified:

- Exact duplicate rows
- Duplicate order IDs with conflicting information

Actions:

- Exact duplicates removed
- Conflicting duplicates flagged for review

### 5. Missing Value Treatment

- Missing region filled with "Unknown"
- Missing ship mode filled with "Unknown"
- Missing discount treated as 0 when valid

### 6. Calculated Columns Created

- cleaned_discount
- calculated_sales
- calculated_profit
- profit_margin
- shipping_delay_days
- order_month
- order_year
- data_quality_flag

---

## Business Rules Applied

| Rule | Action Taken |
|--------|-------------|
| Missing region | Filled with Unknown |
| Missing ship mode | Filled with Unknown |
| Missing discount | Treated as 0 |
| Negative discount | Flagged as invalid |
| Discount above allowed range | Flagged |
| Cancelled orders | Excluded from completed sales summary |
| Failed payments | Excluded from completed sales summary |
| Refunded orders | Summarized separately |
| Ship date before order date | Flagged as invalid |

---

## Summary of Data Quality Issues Found

- Missing values
- Duplicate records
- Invalid discounts
- Date inconsistencies
- Shipping delay issues
- Order status inconsistencies
- Sales calculation mismatches

Records were categorized as:

- Clean
- Warning
- Invalid

---

## Summary of Final Pivot Reports

- Sales and Profit by Region
- Sales and Profit by Category and Sub-Category
- Order Count by Ship Mode
- Profit Margin by Customer Segment
- Refunded/Cancelled/Failed Orders by Region
- Monthly Sales Trend

---

## Key Business Insights

- Some regions generated higher sales and profits.
- Certain categories produced lower profit margins.
- Standard shipping mode accounted for most orders.
- Refunds and cancelled orders reduced profitability.
- Data quality issues were mainly related to discounts and dates.

---

## Assumptions and Limitations

### Assumptions

- Missing regions were replaced with "Unknown".
- Missing ship modes were replaced with "Unknown".
- Missing discounts were treated as 0 when valid.
- Conflicting duplicates were flagged instead of deleted.

### Limitations

- Some business rules were assumed.
- Flagged records require manual review.
- External validation sources were unavailable.

---

## Screenshots Included

- raw_data_preview.png
- cleaned_data_preview.png
- pivot_summary_1.png
- pivot_summary_2.png

---