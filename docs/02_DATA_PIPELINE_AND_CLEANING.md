# Data Pipeline and Relational Cleaning Architecture

## 1. Source Entity Architecture
The raw Olist schema consists of 9 relational tables:
- orders (99,441 rows): Primary transaction timestamps and statuses.
- order_items (112,650 rows): Item prices, freight values, and seller assignments.
- order_payments (103,886 rows): Payment methods, installments, and transaction values.
- order_reviews (100,000 rows): 1-5 star ratings, creation dates, and text comments.
- customers (99,441 rows): Zip code prefixes, states, and customer unique IDs.
- products (32,951 rows): Dimensions, weight (g), and category identifiers.
- sellers (3,095 rows): Seller states and geographic prefixes.
- geolocation (1,000,163 rows): Zip prefixes, latitudes, and longitudes.
- category_translation (71 rows): Portuguese to English category mappings.

---

## 2. Ingestion and Transformation Rules

`
Raw 9-Table Relational Schema
         |
         |-- Filter: order_status == 'delivered' (96,478 orders)
         |-- Aggregate: items -> order grain (price sum, freight sum, seller count)
         |-- Aggregate: payments -> order grain (total value, max installments, primary type)
         |-- Deduplicate: reviews -> latest review per order_id
         |-- Spatial Mean: geolocation -> 1 mean lat/lng per zip prefix
         +-- Join: products -> English translation (fill missing with 'unknown')
         |
         v
Master Order Table (df): 96,478 rows x Order Grain
Item Master Table (item_full): 112,650 rows x Item Grain
`

1. **Order Grain Normalization:** Both order items and payment installments were rolled up to order level. Multiple item lines and multiple payment methods are summed to prevent row-multiplication errors in regression analysis.
2. **Terminal Delivery Cohort Filter:** Delivered orders (96,478) were isolated for delivery-time models. Unfulfilled and canceled orders lack terminal delivery timestamps by definition.
3. **Customer Entity Distinction:** All repeat customer analysis utilizes customer_unique_id (the person token) rather than customer_id (the checkout session token).
4. **Geolocation Spatial Aggregation:** Multiple GPS readings per zip code were collapsed to their arithmetic mean coordinate centroid.
