# Cleaning log

### Project Overview
This document summarizes all cleaning activities, validation checks, business rules, assumptions, and limitations applied to the retail order dataset.

---

# 1. Issues Found
The following data quality issues were identified in the raw dataset:

### Text Issues
- Leading and trailing spaces
- Multiple spaces between words
- Inconsistent capitalization
- Similar values written differently
- Unwanted special characters

### Date Issues
- Missing order dates
- Missing ship dates
- Invalid date values
- Ship dates earlier than order dates

### Missing Values
- Missing region values
- Missing ship mode values
- Missing discount values

### Duplicate Issues
- Exact duplicate rows
- Duplicate order IDs with conflicting information

### Discount Issues
- Negative discount values
- Discount values outside the acceptable range

### Order Status Issues
- Cancelled orders
- Refunded orders
- Failed payment records

### Calculation Issues
- Sales and profit mismatches
- Invalid shipping delays

---

# 2. Cleaning Actions Performed

## Text Standardization

Cleaned and standardized the following columns:
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
- Removed leading spaces
- Removed trailing spaces
- Removed extra spaces
- Standardized text capitalization
- Removed unwanted special characters
- Corrected inconsistent category names

---

## Date Cleaning

Standardized:
- order_date
- ship_date

Validated:
- Missing dates
- Invalid dates
- Non-date text values
- Ship date before order date

Created:
- shipping_delay_days

---

## Duplicate Handling

Identified:
- Exact duplicate rows
- Duplicate order IDs

Actions:
- Exact duplicate rows were identified.
- Conflicting duplicate order IDs were flagged for review.
- No duplicate records were deleted silently.

---

# 3. Business Rules Applied

| Rule | Action Taken |
|--------|-------------|
| Missing region | Filled with "Unknown" |
| Missing ship mode | Filled with "Unknown" |
| Missing discount | Treated as 0 when sales fields were valid |
| Negative discount | Flagged as invalid |
| Discount above allowed range | Flagged as invalid |
| Cancelled orders | Excluded from completed sales summary |
| Failed payments | Excluded from completed sales summary |
| Refunded orders | Summarized separately |
| Ship date before order date | Flagged as invalid shipping record |

---

# 4. Calculated Columns Created

The following columns were added:
- cleaned_discount
- calculated_sales
- calculated_profit
- profit_margin
- shipping_delay_days
- order_month
- order_year
- data_quality_flag

Additional column:
- duplicate_flag

---

# 5. Assumptions Made

- Missing region values were replaced with "Unknown".
- Missing ship mode values were replaced with "Unknown".
- Missing discount values were assumed to be 0 only when other sales fields were valid.
- Duplicate records with conflicting information were flagged instead of removed.
- Invalid records were retained for manual review.

---

# 6. Records Removed

- Exact duplicate records removed: 0
- Conflicting duplicate records removed: 0

No records were deleted silently.

---

# 7. Records Flagged

Records were flagged for:

### Duplicate Issues

- Duplicate order IDs

### Discount Issues

- Negative discount values
- Discount values exceeding the valid range

### Date Issues

- Missing dates
- Invalid dates
- Ship date earlier than order date

### Order Issues

- Cancelled orders
- Failed payments
- Refunded orders

### Quality Classification

Records were classified as:
- Clean
- Warning
- Invalid

---

# 8. Limitations of the Cleaning Process

- Some business assumptions were made because no domain documentation was provided.
- Flagged records may require manual review.
- Outlier detection was not performed beyond assignment requirements.
- External reference systems were unavailable for additional validation.
- Duplicate records with conflicting values were retained and flagged rather than deleted.

---

# 9. Summary

The dataset was successfully cleaned and validated.

Major activities included:
- Text Standardization
- Date validation
- Duplicate detection
- Missing value handling
- Discount validation
- Creation of calculated columns
- Data quality classification
- Pivot summary generation
- Business rule implementation

The resulting dataset is analysis-ready and suitable for business reporting and decision-making.
