# Data Mart Project: RFM Customer Segmentation

## Table of Contents
- [Introduction](#introduction)
- [Data Mart Details](#data-mart-details)
  - [Data Mart Name](#data-mart-name)
  - [Data Mart Location](#data-mart-location)
  - [Data Source Location](#data-source-location)
  - [Data Mart Structure](#data-mart-structure)
  - [Data Mart Depth](#data-mart-depth)
  - [Data Updates](#data-updates)
  - [Data Quality Requirements](#data-quality-requirements)
- [Data Source Structure](#data-source-structure)
  - [Input Data](#input-data)
  - [Fields](#fields)
    - [Orders Table](#orders-table)
    - [Products Table](#products-table)
    - [Order Items Table](#order-items-table)
    - [Order Status Log Table](#order-status-log-table)
    - [Order Statuses Table](#order-statuses-table)
    - [Users Table](#users-table)
- [Output Data](#output-data)
  - [RFM Segments Calculation](#rfm-segments-calculation)
  - [Data Mart Depth](#data-mart-depth-1)
  - [Data Updates](#data-updates-1)
  - [Data Quality Requirements](#data-quality-requirements-1)

## Introduction

This project aims to create a Data Mart for RFM Customer Segmentation, providing valuable insights into customer behavior and spending patterns.

## Data Mart Details

### Data Mart Name

- **dm_rfm_segments**

### Data Mart Location

- **de.analysis**

### Data Source Location

- **de.production**

### Data Mart Structure

| **Field Name**    | **Data Type**    | **Description**                     |
|-------------------|------------------|-------------------------------------|
| user_id           | _int4_           | Unique identifier for each user     |
| recency           | _int4_           | Number of days since the last order |
| frequency         | _int4_           | Number of orders                    |
| monetary_value    | _numeric(19, 5)_ | Total customer spend                |

### Data Mart Depth

- 2022-01-01 - 2022-12-31

### Data Updates

- No updates required

### Data Quality Requirements

- A successful order is an order with the status "Closed."
- Segment users into 5 equal RFM segments, even if the number of orders is equal.

## Data Source Structure

### Input Data

#### Orders Table

| **Field Name**    | **Data Type**    | **Description**                  |
|-------------------|------------------|----------------------------------|
| order_id          | _int4_           | Unique identifier for each order |
| order_ts          | _timestamp_      | Order timestamp                  |
| user_id           | _int4_           | User ID                          |
| bonus_payment     | _numeric(19, 5)_ | Bonus payment amount             |
| payment           | _numeric(19, 5)_ | Payment amount                   |
| cost              | _numeric(19, 5)_ | Order cost                       |
| bonus_grant       | _numeric(19, 5)_ | Bonus grant amount               |
| status            | _int4_           | Order status                     |

#### Products Table

| **Field Name**    | **Data Type**    | **Description**                    |
|-------------------|------------------|------------------------------------|
| id                | _int4_           | Unique identifier for each product |
| name              | _varchar(2048)_  | Product name                       |
| price             | _numeric(19, 5)_ | Product price                      |

#### Order Items Table

| **Field Name**    | **Data Type**    | **Description**                       |
|-------------------|------------------|---------------------------------------|
| id                | _int4_           | Unique identifier for each order item |
| product_id        | _int4_           | Product ID                            |
| order_id          | _int4_           | Order ID                              |
| name              | _varchar(2048)_  | Order item name                       |
| price             | _numeric(19, 5)_ | Order item price                      |
| discount          | _numeric(19, 5)_ | Order item discount                   |
| quantity          | _int4_           | Quantity of order items               |

#### Order Status Log Table

| **Field Name**    | **Data Type**    | **Description**                                   |
|-------------------|------------------|---------------------------------------------------|
| id                | _int4_           | Unique identifier for each order status log entry |
| order_id          | _int4_           | Order ID                                          |
| status_id         | _int4_           | Order status ID                                   |
| dttm              | _timestamp_      | Status change timestamp                           |

#### Order Statuses Table

| **Field Name**    | **Data Type**    | **Description**                         |
|-------------------|------------------|-----------------------------------------|
| id                | _int4_           | Unique identifier for each order status |
| key               | _varchar(255)_   | Order status key                        |

#### Users Table

| **Field Name**    | **Data Type**    | **Description**                 |
|-------------------|------------------|---------------------------------|
| id                | _int4_           | Unique identifier for each user |
| name              | _varchar(2048)_  | User name                       |
| login             | _varchar(2048)_  | User login                      |

### Output Data

#### RFM Segments Calculation

| **Field Name**    | **Data Type**    | **Description**                     |
|-------------------|------------------|-------------------------------------|
| user_id           | _int4_           | Unique identifier for each user     |
| recency           | _int4_           | Number of days since the last order |
| frequency         | _int4_           | Number of orders                    |
| monetary_value    | _numeric(19, 5)_ | Total customer spend                |

### Data Mart Depth

- 2022-01-01 - 2022-12-31

### Data Updates

- No updates required

### Data Quality Requirements

- A successful order is an order with the status "Closed."
- Segment users into 5 equal RFM segments, even if the number of orders is equal.
