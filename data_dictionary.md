# Data Dictionary — TikTok Shop Affiliate Creator Performance

This describes the four files in `/data`. The files relate to each other:
**a creator has many videos; a video can drive many orders.** Join carefully so you
don't count the same revenue twice.

```
creators.csv ──< videos.csv ──< orders.csv >── products.csv
 (creator)        (video)         (order line)     (product)
   creator_id ─────┘   │            │   └─── sku_id ──┘
                       └── video_id ┘
```

All tables join on **`creator_id`**, **`video_id`**, and **`sku_id`** / **`product_id`**.

---

## `creators.csv` — one row per creator

The roster of creators in the affiliate program.

| Column | Type | Description |
|---|---|---|
| `creator_id` | text | Stable identifier for the creator. **Primary key**; used to link to `videos` and `orders`. |
| `creator_username` | text | The creator's TikTok handle (partially masked for privacy). |
| `follower_count` | number | Approximate follower count at time of export. |
| `niche` | text | The creator's primary content category (e.g. Wellness, Fitness, Nutrition). |
| `state` | text | US state the creator primarily sells into. |
| `commission_rate` | number | The creator's commission rate, as a decimal fraction (e.g. `0.15` = 15%). |
| `join_date` | date | When the creator joined the affiliate program. |
| `status` | text | Current standing in the program. |

---

## `videos.csv` — one row per video

Per-video content and engagement metrics.

| Column | Type | Description |
|---|---|---|
| `video_id` | text | Unique identifier for the video. **Primary key.** |
| `creator_id` | text | The creator who posted the video. Links to `creators.creator_id`. |
| `post_date` | date | When the video was posted. |
| `views` | number | Times the shoppable video was shown / viewed. |
| `likes` | number | Likes on the video. |
| `comments` | number | Comments on the video. |

---

## `orders.csv` — one row per order line

Attributed transactions. A single order can span **multiple lines** (one per product),
so the same `order_id` may appear on more than one row. **Primary key: (`order_id`,
`sku_id`).**

| Column | Type | Description |
|---|---|---|
| `order_id` | text | Identifier for the order. Repeats across lines of the same multi-product order. |
| `creator_id` | text | The creator credited with the sale. Links to `creators.creator_id`. |
| `video_id` | text | The content credited with driving the order. Links to `videos.video_id`. |
| `content_type` | text | How the sale was attributed. |
| `sku_id` | text | The product variant sold. Links to `products.sku_id`. |
| `product_id` | text | The parent product. Links to `products.product_id`. |
| `quantity` | number | Units sold on this line. |
| `gross_sales` | currency | Gross merchandise value for this line, before any returns or cancellations. |
| `order_status` | text | The current state of the order. |
| `order_date` | datetime | When the order was placed. |
| `commission_rate` | number | The commission rate applied to this order. |
| `commission_paid` | currency | Commission earned on this order line. |

---

## `products.csv` — one row per product (SKU)

The product catalog.

| Column | Type | Description |
|---|---|---|
| `sku_id` | text | Product variant identifier. **Primary key**; links to `orders.sku_id`. |
| `product_id` | text | Parent product identifier; links to `orders.product_id`. |
| `product_name` | text | Display name of the product. |
| `category` | text | Product category. |

---

*If anything here is ambiguous, note your assumption and proceed — stating reasonable
assumptions is part of the exercise.*
