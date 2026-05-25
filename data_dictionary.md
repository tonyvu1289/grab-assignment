# Data Dictionary — `grab_vn_case.db`

**Format:** SQLite
**Coverage:** 2024-01-01 to 2024-04-07 (14 weeks)
**Cities:** Ho Chi Minh City, Da Nang, Hanoi

---

## Tables

### `users`

One row per registered user.

| Column | Type | Description |
|---|---|---|
| `user_id` | INTEGER | Unique user identifier |
| `city` | TEXT | City of the user |
| `payment_preference` | TEXT | User's preferred payment method at registration |
| `user_segment` | TEXT | Behavioural segment assigned at registration |
| `registration_date` | TEXT | Date of account creation (ISO 8601) |

**Distinct values**

`city`: `Ho Chi Minh City`, `Da Nang`, `Hanoi`

`payment_preference`: `Cash`, `ZaloPay`, `Card`

`user_segment`: `Voucher Hunter`, `Regular`, `Occasional`, `High Value`

---

### `weather_daily`

One row per city per day.

| Column | Type | Description |
|---|---|---|
| `date` | TEXT | Date (ISO 8601) |
| `city` | TEXT | City name |
| `rainfall_mm` | REAL | Total rainfall in millimetres |
| `rain_category` | TEXT | Categorical classification of rainfall intensity |

**Distinct values**

`rain_category`: `None`, `Light`, `Moderate`, `Heavy`

---

### `transactions`

One row per transaction.

| Column | Type | Description |
|---|---|---|
| `transaction_id` | INTEGER | Unique transaction identifier |
| `date` | TEXT | Transaction date (ISO 8601) |
| `week_number` | INTEGER | Week number relative to dataset start (1–14) |
| `period` | TEXT | Named period the transaction falls within |
| `city` | TEXT | City where the transaction occurred |
| `service_type` | TEXT | Grab service used |
| `user_id` | INTEGER | Foreign key referencing `users.user_id` |
| `payment_type` | TEXT | Payment method used for this transaction |
| `gross_gmv_k_vnd` | REAL | Gross transaction value in VND thousands, before any discount |
| `discount_k_vnd` | REAL | Discount amount applied in VND thousands |
| `net_gmv_k_vnd` | REAL | Net transaction value in VND thousands, after discount |
| `voucher_applied` | INTEGER | `1` if a voucher was redeemed, `0` otherwise |
| `rainfall_mm` | REAL | Rainfall in millimetres on the transaction date and city |

**Distinct values**

`period`: `Pre-Promo`, `Promo`, `Post-Promo`

`service_type`: `GrabBike`, `GrabCar`, `GrabFood`

`payment_type`: `Cash`, `ZaloPay`, `Card`

---

### View: `daily_gmv_summary`

Pre-aggregated daily rollup of `transactions`, grouped by date, city, service type, and payment type.

| Column | Type | Description |
|---|---|---|
| `date` | TEXT | Date (ISO 8601) |
| `week_number` | INTEGER | Week number (1–14) |
| `period` | TEXT | Named period |
| `city` | TEXT | City name |
| `service_type` | TEXT | Grab service |
| `payment_type` | TEXT | Payment method |
| `net_gmv_k_vnd` | REAL | Sum of net GMV in VND thousands |
| `gross_gmv_k_vnd` | REAL | Sum of gross GMV in VND thousands |
| `total_discount_k_vnd` | REAL | Sum of discounts in VND thousands |
| `n_transactions` | INTEGER | Count of transactions |
| `n_voucher_redemptions` | INTEGER | Count of transactions where a voucher was applied |

---

## Notes

- All monetary values are in **VND thousands**. Divide by 1,000 to convert to millions.
- `transactions.rainfall_mm` is denormalised from `weather_daily` for convenience. Both columns contain the same values.
- `week_number` starts at 1 on 2024-01-01. Each increment represents 7 calendar days.
- The promo period covers weeks 7–12 (2024-02-12 to 2024-03-24).
