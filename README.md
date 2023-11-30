# Data Mart project
----
## Data Mart for RFM Customer Segmentation
### Data Mart Name: _dm_rfm_segments_

#### Data Mart Location: _de.analysis_

#### Data Source Location: _de.production_

#### Data Mart Structure:

| **Field Name** | **Data Type**    | **Description**                     |
|----------------|------------------|-------------------------------------|
| user_id        | _int4_           | Unique identifier for each user     |
| recency        | _int4_           | Number of days since the last order |
| frequency      | _int4_           | Number of orders                    |
| monetary_value | _numeric(19, 5)_ | Total customer spend                |

#### Data Mart Depth: 2022-01-01 - 2022-12-31

#### Data Updates: No updates required

#### Data Quality Requirements:

A successful order is an order with the status "Closed"
Segment users into 5 equal RFM segments, even if the number of orders is equal
Data Source Structure
Requirements for the RFM Customer Segmentation Data Mart

### Input Data:

| **Table Name** | **Description**      |
|----------------|----------------------|
| orders         | Order information    |
| products       | Product information  |
| orderitems     | Ordered items        |
| orderstatuslog | Order status history |
| orderstatuses  | Order status types   |
| users          | User information     |

#### Fields:

#### _orders table_
| **Field Name** | **Data Type**  | **Description**                  |
|----------------|----------------|----------------------------------|
| order_id       | int4           | Unique identifier for each order |
| order_ts       | timestamp      | Order timestamp                  |
| user_id        | int4           | User ID                          |
| bonus_payment  | numeric(19, 5) | Bonus payment amount             |
| payment        | numeric(19, 5) | Payment amount                   |
| cost           | numeric(19, 5) | Order cost                       |
| bonus_grant    | numeric(19, 5) | Bonus grant amount               |
| status         | int4           | Order status                     |

#### _products table_
| **Field Name** | **Data Type**  | **Description**                    |
|----------------|----------------|------------------------------------|
| id             | int4           | Unique identifier for each product |
| name           | varchar(2048)  | Product name                       |
| price          | numeric(19, 5) | Product price                      |

#### _orderitems table_
| **Field Name** | **Data Type**  | **Description**                       |
|----------------|----------------|---------------------------------------|
| id             | int4           | Unique identifier for each order item |
| product_id     | int4           | Product ID                            |
| order_id       | int4           | Order ID                              |
| name           | varchar(2048)  | Order item name                       |
| price          | numeric(19, 5) | Order item price                      |
| discount       | numeric(19, 5) | Order item discount                   |
| quantity       | int4           | Quantity of order items               |

#### _orderstatuslog table_
| **Field Name** | **Data Type** | **Description**                                   |
|----------------|---------------|---------------------------------------------------|
| id             | int4          | Unique identifier for each order status log entry |
| order_id       | int4          | Order ID                                          |
| status_id      | int4          | Order status ID                                   |
| dttm           | timestamp     | Status change timestamp                           |

#### _orderstatuses table_
| **Field Name** | **Data Type** | **Description**                         |
|----------------|---------------|-----------------------------------------|
| id             | int4          | Unique identifier for each order status |
| key            | varchar(255)  | Order status key                        |

#### _users table_
| **Field Name** | **Data Type** | **Description**                 |
|----------------|---------------|---------------------------------|
| id             | int4          | Unique identifier for each user |
| name           | varchar(2048) | User name                       |
| login          | varchar(2048) | User login                      |

### Output Data:

The data mart will calculate the RFM segments for each customer. The RFM segments are calculated as follows:

| **Field Name** | **Data Type**    | **Description**                     |
|----------------|------------------|-------------------------------------|
| user_id        | _int4_           | Unique identifier for each user     |
| recency        | _int4_           | Number of days since the last order |
| frequency      | _int4_           | Number of orders                    |
| monetary_value | _numeric(19, 5)_ | Total customer spend                |

Data Mart Depth: 2022-01-01 - 2022-12-31

Data Updates: No updates required

#### Data Quality Requirements:
A successful order is an order with the status "Closed".
Segment users into 5 equal RFM segments, even if the number of orders is equal.
