# de1-Term2

This repository contains our work for the Data Engineering 1: SQL and Different Shapes of Data course. The Term Project 2 uses data from the Brazilian E-Commerce Public Dataset by Olist.

Project Title: Brazilian E-Commerce Public Dataset Analysis

## Usage Instructions

1. **Clone the repository:**
   ```bash
   git clone 


## Repository Structure

The repository is organized as follows:
- **`Term2/`**: Main project folder.
  - **`data/`**: Contains CSV files with raw data.
    - `olist_customers_dataset.csv`: Data related to clients.
    - `olist_geolocation_dataset.csv`: Data related to geolocation.
    - `olist_order_items_dataset.csv`: Data related to ordered items.
    - `olist_order_payments_dataset.csv`: Data related to payments.
    - `olist_order_reviews_dataset.csv`: Data related to reviews on orders.
    - `olist_orders_dataset.csv`: Data related to orders.
    - `olist_products_dataset.csv`: Data related to products.
    - `olist_sellers_dataset.csv`: Data related to sellers on the ecommerce platform.
    - `product_category_name_translation.csv`: English translations of product categories.
  - **`script/`**: Contains scripts, codes used in the project.
    - `term-project-2.knwf`: Knime workflow file.
  - **`EER.jpeg`**: EER.
  - **`Report_Team1.pdf`**: The documentation file.
  - **`Presentation_Team1.pdf`**: Presentation file.

- **`README.md`**: This file, which contains the brief documentation for the project.


## Data Description
Tables:

olist_customers_dataset.csv table contains information on clients:
| Column                   | Description                                             |
|--------------------------|---------------------------------------------------------|
| customer_id              | Key to the orders dataset. Each order has a unique customer_id. |
| customer_unique_id       | Unique identifier for the customer.    |
| customer_zip_code_prefix | First five digits of customer zip code.  |
| customer_city            | City associated with the customer's location.          |
| customer_state           | State associated with the customer's location.         |


olist_geolocation_dataset.csv table contains information about geolocation.
| Column                     | Description                                                  |
|----------------------------|--------------------------------------------------------------|
| customer_zip_code_prefix   | First five digits of customer zip code.  |
| geolocation_lat            | Latitude of the location.                        |
| geolocation_lng            | Longitude of the location.                       |
| geolocation_city           | City name.               |
| geolocation_state          | State name.              |

olist_order_items_dataset.csv table contains information about ordered items.
| Column                     | Description                                                  |
|----------------------------|--------------------------------------------------------------|
| order_id                   | Unique identifier for the order.                        |
| order_item_id | sequential number identifying number of items included in the same order. |
| product_id            | Unique identifier for the product.                  |
| seller_id           | Unique identifier for the seller.         |
| shipping_limit_date | The seller's shipping limit date for handling the order over to the logistic partner. |
| price          | Item price.              |
| freight_value          | Item freight value item (if an order has more than one item the freight value is splitted between items).     |

olist_order_payments_dataset.csv table contains information about payments.
| Column                     | Description                                              |
|----------------------------|----------------------------------------------------------|
| order_id                   | Unique identifier for the order.                        |
| payment_sequential         | A customer may pay an order with more than one payment method. If he does so, a sequence will be created to accommodate all payments.   |
| payment_type               | Method of payment chosen by the customer.    |
| payment_installments       | Number of installments chosen by the customer.          |
| payment_value              | Transaction value.                             |

olist_order_reviews_dataset.csv table contains reviews on orders.
| Column                     | Description                                                  |
|----------------------------|--------------------------------------------------------------|
| review_id   | Unique identifier for the review.   |
| order_id            | Unique identifier for the order.                          |
| review_score  | Note ranging from 1 to 5 given by the customer on a satisfaction survey.  |
| review_comment_title | Comment title from the review left by the customer, in Portuguese. |
| review_comment_message | Comment message from the review left by the customer, in Portuguese. |
| review_creation_date  | Shows the date in which the satisfaction survey was sent to the customer.  |
| review_answer_timestamp  | Shows satisfaction survey answer timestamp.  |

olist_orders_dataset.csv table contains information about orders.
| Column                     | Description                                                  |
|----------------------------|--------------------------------------------------------------|
| order_id            | Unique identifier for the order.                             |
| customer_id  | Key to the customer dataset. Each order has a unique customer_id. |
| order_status           | Reference to the order status (delivered, shipped, etc).  |
| order_purchase_timestamp          | Shows the purchase timestamp.    |
| order_approved_at  | Shows the payment approval timestamp.   |
| order_delivered_carrier_date     | Shows the order posting timestamp. When it was handled to the logistic partner. |
| order_delivered_customer_date  | Shows the actual order delivery date to the customer. |
| order_estimated_delivery_date| Shows the estimated delivery date that was informed to customer at the purchase moment. |

olist_products_dataset.csv table contains information about products.
| Column                     | Description                                                  |
|----------------------------|--------------------------------------------------------------|
| product_id            | Unique identifier for the product.                            |
| product_category_name            | Root category of product, in Portuguese.              |
| product_name_length           | Number of characters extracted from the product name.     |
| product_description_length  | Number of characters extracted from the product description. |
| product_photos_qty | Number of published photos of the product.    |
| product_weight_g     | Product weight measured in grams.              |
| product_length_cm  | Product length measured in centimeters.              |
| product_height_cm | Product height measured in centimeters.              |
| product_width_cm | Product width measured in centimeters.              |

olist_sellers_dataset.csv table contains information about sellers on the ecommerce platform.
| Column                     | Description                                                  |
|----------------------------|--------------------------------------------------------------|
| seller_id            | Unique identifier for the seller.                        |
| seller_zip_code_prefix          | First five digits of customer zip code.  |
| seller_city           | Seller city name.          |
| seller_state          | Seller state.        |

product_category_name_translation.csv table contains translations of product categories.
| Column                     | Description                                                  |
|----------------------------|--------------------------------------------------------------|
| product_category_name            | Category name in Portuguese.                        |
| product_category_name_english    | Category name in English.                       |
