# 📊 DAX Measures

## 1) Orders & Delivery Performance

### Orders
Counts unique orders.
```DAX
Orders :=
DISTINCTCOUNT ( fact_orders[order_id] )
```

### Delivered Orders
Orders with status Delivered.
```
Delivered Orders :=
CALCULATE ( [Orders], fact_orders[is_delivered] = TRUE() )
```

### Late Delivered Orders
Delivered orders that were late.
```
Late Delivered Orders :=
CALCULATE (
    [Orders],
    fact_orders[is_delivered] = TRUE(),
    fact_orders[is_late] = TRUE()
)
```

### Late Delivery %
Share of late deliveries among delivered orders.
```
Late Delivery % :=
DIVIDE ( [Late Delivered Orders], [Delivered Orders], 0 )
```

### Avg Delivery Days
Average delivery duration for delivered orders.
```
Avg Delivery Days :=
AVERAGEX (
    FILTER ( fact_orders, fact_orders[is_delivered] = TRUE() ),
    fact_orders[delivery_days]
)
```

### Avg Delay Days (Late Only)
Average delay (in days) for late delivered orders.
```
Avg Delay Days (Late Only) :=
AVERAGEX (
    FILTER (
        fact_orders,
        fact_orders[is_delivered] = TRUE()
            && fact_orders[is_late] = TRUE()
    ),
    fact_orders[delivery_delay_days]
)
```

## 2) Revenue (GMV) & Risk

### GMV
Gross merchandise value (sum of item revenue).
```
GMV :=
SUMX ( fact_order_items, fact_order_items[item_revenue] )
```

### GMV (Delivered)
GMV for delivered orders.
```
GMV (Delivered) :=
CALCULATE ( [GMV], fact_orders[is_delivered] = TRUE() )
```

### GMV (Late Delivered)
GMV for delivered late orders.
```
GMV (Late Delivered) :=
CALCULATE (
    [GMV],
    fact_orders[is_delivered] = TRUE(),
    fact_orders[is_late] = TRUE()
)
```

### GMV at Risk % (Late Share)
Share of delivered GMV associated with late deliveries.
```
GMV at Risk % (Late Share) :=
DIVIDE ( [GMV (Late Delivered)], [GMV (Delivered)], 0 )
```

## 3) Reviews & Customer Satisfaction

### Avg Review Score
Average review score (1–5).
```
Avg Review Score :=
AVERAGE ( fact_reviews[review_score] )
```

### Reviewed Orders
Count of orders that have at least one review.
```
Reviewed Orders :=
DISTINCTCOUNT ( fact_reviews[order_id] )
```

### Low Rating Orders
Count of orders with low rating flag (e.g., 1–2 stars depending on your logic).
```
Low Rating Orders :=
CALCULATE (
    DISTINCTCOUNT ( fact_reviews[order_id] ),
    fact_reviews[is_low_rating] = TRUE()
)
```

### Low Rating %
Share of low-rated orders among reviewed orders.
```
Low Rating % :=
DIVIDE ( [Low Rating Orders], [Reviewed Orders], 0 )
```

### Low Rating % (Late)
Low rating share for late delivered orders.
```
Low Rating % (Late) :=
CALCULATE (
    [Low Rating %],
    fact_orders[is_delivered] = TRUE(),
    fact_orders[is_late] = TRUE()
)
```

### Low Rating % (On Time)
Low rating share for on-time delivered orders.
```
Low Rating % (On Time) :=
CALCULATE (
    [Low Rating %],
    fact_orders[is_delivered] = TRUE(),
    NOT ( fact_orders[is_late] )
)
```

### Rating Gap (Late - On Time)
Difference in low rating share: Late minus On-Time.
```
Rating Gap (Late - OnTime) :=
[Low Rating % (Late)] - [Low Rating % (On Time)]
```

- **Definition of Low Rating**: `review_score <= 2`
- **Late logic**: `delivered_date > estimated_date`
- **Delay bucket**: enumeration of intervals