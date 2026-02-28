Orders :=
DISTINCTCOUNT ( fact_orders[order_id] )

Delivered Orders :=
CALCULATE ( [Orders], fact_orders[is_delivered] = TRUE() )

Late Delivered Orders :=
CALCULATE ( [Orders], fact_orders[is_late] = TRUE() )

Late Delivery % :=
DIVIDE ( [Late Delivered Orders], [Delivered Orders] )

Avg Delivery Days :=
AVERAGEX (
    FILTER ( fact_orders, fact_orders[is_delivered] = TRUE() ),
    fact_orders[delivery_days]
)

Avg Delay Days (Late Only) :=
AVERAGEX (
    FILTER ( fact_orders, fact_orders[is_late] = TRUE() ),
    fact_orders[delivery_delay_days]
)

GMV :=
SUMX ( fact_order_items, fact_order_items[item_revenue] )

GMV (Delivered) :=
CALCULATE ( [GMV], fact_orders[is_delivered] = TRUE() )

GMV (Late Delivered) :=
CALCULATE ( [GMV], fact_orders[is_late] = TRUE() )

GMV at Risk % (Late Share) :=
DIVIDE ( [GMV (Late Delivered)], [GMV (Delivered)] )

Avg Review Score :=
AVERAGE ( fact_reviews[review_score] )

Low Rating Orders :=
CALCULATE (
    DISTINCTCOUNT ( fact_reviews[order_id] ),
    fact_reviews[is_low_rating] = TRUE()
)

Reviewed Orders :=
DISTINCTCOUNT ( fact_reviews[order_id] )

Low Rating % :=
DIVIDE ( [Low Rating Orders], [Reviewed Orders] )

Low Rating % (Late) :=
CALCULATE ( [Low Rating %], fact_orders[is_late] = TRUE() )

Low Rating % (On Time) :=
CALCULATE ( [Low Rating %], fact_orders[is_late] = FALSE() )

Rating Gap (Late - OnTime) :=
[Low Rating % (Late)] - [Low Rating % (On Time)]