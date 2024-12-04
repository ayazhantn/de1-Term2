# de1-Term2

This repository contains our work for the ECBS 5146 Data Engineering 1: SQL and Different Shapes of Data course.
The Term Project 2 uses data from the Brazilian E-Commerce Public Dataset by Olist.
Project Title: Brazilian E-Commerce Public Dataset Analysis

## Usage Instructions

0. Prerequisites:

   - Knime

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ayazhantn/de1-Term2

 # Table of Contents
1. [Repository Structure](#repository-structure)
2. [Project Overview](#project-overview)
3. [Data Description](#data-description)
4. [Research Questipns](#research-questions)
5. [ETL Pipeline Design](#etl-pipeline-design)
6. [Visualizations](#visualizations)
7. [Conclusion and Future Work](#conclusion-and-future-work)

# Repository Structure

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
  - **`script/`**: Contains Python code and Knime workflow used in the project.
    - `mongo.ipynb`: Python script for importing data.
    - `term-project-2.knwf`: Knime workflow file.
  - **`EER.jpeg`**: EER.
  - **`Knime_workflow.jpeg`**: ETL Pipeline in Knime.
  - **`visuals/`**: Contains visualisations answering Research Questions.
    - `Q1Chart.jpeg`: Chart for Q1.
    - `Q2Chart.jpeg`: Chart for Q2.
    - `Q3ChartA.jpeg`: Chart A for Q3.
    - `Q3ChartB.jpeg`: Chart B for Q3.
    - `Q4Chart.jpeg`: Chart for Q4.
  - **`Report_Team1.pdf`**: The documentation file.
  - **`Presentation_Team1.pdf`**: Presentation file.

- **`README.md`**: This file, which contains the brief documentation for the project.

 # Project Overview

The goal of this project is to apply knowledge and skills learned during the Data Engineering 1: SQL and Different Shapes of Data course. The project involves building an ETL pipeline in Knime, setting research questions and analyzing them to get insights about customer behavior and sales trends from the Brazilian E-Commerce Dataset.

 # Data Description
Source: Kaggle - [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

The dataset contains details of 100,000 orders placed across various marketplaces in Brazil between 2016 and 2018.
 
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

![EER](Term2/EER.jpeg)

# ETL Pipeline Design
The ETL pipeline involves different steps:

Data Import and Joining

- MongoDB Reader: Reads data from the MongoDB database, allowing us to retrieve information from the various collections.
- JSON to Table: Converts data in JSON format into structured tabular data for making the analysis easier.


Data Transformation and Cleaning

- Different filtering, manipulation, grouping, sampling, sorting and difference calculation (e.g. Date&Time Difference) nodes were used depending on the Research Question analysis demand.


Data Joining and Enrichment

- Joiner, GeoFile Reader and JSON Path nodes were used for matching columns and enriching data with API, JSON files. Geospatial Analytics extension was an additional tool.


Analysis and Visualization

- Bar Chart (JavaScript), Rule Engine, Geospatial View were used to visualize trends and geographic patterns in the data and apply logical rules for categorization. As a result, clear representations of trends and research question answers are obtained.
  

# Research Questions
Q1. How does the delivery performance (on-time vs. delayed) affect customer sentiment in Brazilian e-commerce?

Q2. Is there a clear seasonal trend in order volume? How to promote off-season sales?

Q3. Which categories perform best and worst nationwide?

Q4. Are there noticeable regional differences in the delivery periods?


# Visualizations & Answers to Research Questions

Q1. How does the delivery performance (on-time vs. delayed) affect customer sentiment in Brazilian e-commerce?

![Q1Chart](Term2/visuals/Q1Chart.jpeg)


Q2. Is there a clear seasonal trend in order volume? How to promote off-season sales?

![Q2Chart](Term2/visuals/Q2Chart.jpeg)

1. Analysis of Seasonal Order Trends
From the bar chart, we can clearly see the differences in order quantities across different seasons：
- Winter has the highest order volume, nearing 30,573 orders, indicating very strong market demand during this season. This is likely due to holiday promotions (e.g., Christmas and New Year sales), where consumers tend to make more purchases.
- Autumn follows closely, with relatively high order numbers, likely driven by autumn promotions and seasonal product demand.
- Summer has a moderate order volume, lower than both autumn and winter but higher than spring. This suggests stable consumer demand during summer, possibly influenced by holidays and leisure travel seasons.
- Spring has the lowest order volume, significantly lower than the other three seasons. This may reflect weaker market demand during spring, possibly due to the absence of major holidays or promotional events, resulting in lower consumer purchasing intent.

2. Conclusions
- Winter and Autumn: These two seasons have higher order volumes, likely due to holiday sales, seasonal promotions, and demand fluctuations. These seasons represent critical sales periods for businesses, and large-scale promotions should be planned in advance.
- Spring Sales Slump: Spring has a significantly lower order volume, which may be attributed to the lack of major holidays or promotional events. This season may require businesses to adopt strategies to boost sales.

3. Strategies to Boost Spring Sales
To increase sales during the spring season, businesses can consider the following strategies:
- Seasonal Promotions: Offer discounts or promotional activities for spring products to attract consumers. For example, a “Spring Clearance” sale could encourage consumers to purchase seasonal products.
- Cross-Season Bundling: Bundle spring products with popular items from other seasons to boost sales. For example, pairing spring clothing with winter products can help drive sales.
- Marketing Campaigns: Spring marketing campaigns may need more targeted efforts. Promotions can be tailored to specific consumer groups via social media, email marketing, and other channels to raise awareness and interest in spring products.
- Limited-Time Promotions: Introduce limited-time offers during specific dates or holidays (e.g., Easter) in spring to encourage consumer purchases.

4. Overall Trends and Recommendations
Overall, businesses should focus on the Autumn and Winter seasons as key sales periods, where heavier promotion efforts can capture consumer spending. For Spring, innovative promotional tactics and strategies are needed to spark consumer interest and prevent low sales from affecting overall business performance.


Q3. Which categories perform best and worst nationwide?

![Q3ChartA](Term2/visuals/Q3ChartA.jpeg)
![Q3ChartB](Term2/visuals/Q3ChartB.jpeg)


Q4. Are there noticeable regional differences in the delivery periods?

![Q4Chart](Term2/visuals/Q4Chart.jpeg)


# Conclusion and Future Work

The project results are helpful for understanding key factors influencing customer behavior and optimizing business strategies in Brazilian e-commerce.

1. Timely Deliveries Matter (Q1): On-time deliveries lead to positive sentiment, while delays often result in negative reviews. This emphasizes the need for efficient logistics.

2. Seasonal Sales Trends (Q2): Winter and Autumn drive high order volumes due to holiday promotions, while Spring requires creative strategies to boost sales.

3. Product Performance (Q3): Least popular product categories might be a sign of low demand and the necessity to give up on them or a sign of getting new shares in the market by improving the sellers' business systems in these areas. More analysis needs to be done to decide which way to go.

4. Regional Delivery Insights (Q4): Delivery delays are more pronounced in northern regions, indicating logistical challenges that need addressing to improve satisfaction.

These insights guide logistics optimization and new marketing strategies for better customer experiences and growth of businesses (sellers).

However, this analysis needs to be deepened with future work. Namely, focus could be on expanding geospatial analytics for delivery optimization, checking time trends over the years (comparing 2016, 2017 and 2018 within each other and with more recent data) and integrating external data sources (e.g., weather, social media trends). This could provide further insights to possible improvements to the Brazilian e-commerce market.
