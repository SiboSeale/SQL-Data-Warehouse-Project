# 📊 Data Catalog for Gold Layer

## 🧾 Overview

The **Gold Layer** is the business-level data representation, structured to support analytical and reporting use cases. It consists of **dimension tables** and **fact tables** capturing key business metrics.

---

## 📁 Tables

### 1. `gold.dim_customers`

**Purpose:**  
Stores customer details enriched with demographic and geographic data.

**Columns:**

| Column Name       | Data Type     | Description                                                                 |
|-------------------|---------------|-----------------------------------------------------------------------------|
| `customer_key`    | INT           | Surrogate key uniquely identifying each customer record.                   |
| `customer_id`     | INT           | Unique numerical identifier assigned to each customer.                     |
| `customer_number` | NVARCHAR(50)  | Alphanumeric identifier used for tracking and referencing customers.       |
| `first_name`      | NVARCHAR(50)  | The customer's first name.                                                 |
| `last_name`       | NVARCHAR(50)  | The customer's last name or family name.                                   |
| `country`         | NVARCHAR(50)  | Customer’s country of residence (e.g., "Australia").                       |
| `marital_status`  | NVARCHAR(50)  | Marital status (e.g., "Married", "Single").                                |
| `gender`          | NVARCHAR(50)  | Gender (e.g., "Male", "Female", "n/a").                                    |
| `birthdate`       | DATE          | Date of birth in `YYYY-MM-DD` format.                                      |
| `create_date`     | DATE          | Date the customer record was created.                                      |

---

### 2. `gold.dim_products`

**Purpose:**  
Provides information about products and their associated attributes.

**Columns:**

| Column Name           | Data Type     | Description                                                                     |
|-----------------------|---------------|---------------------------------------------------------------------------------|
| `product_key`         | INT           | Surrogate key uniquely identifying each product.                               |
| `product_id`          | INT           | Unique internal identifier for the product.                                    |
| `product_number`      | NVARCHAR(50)  | Alphanumeric code used for product tracking and categorization.                |
| `product_name`        | NVARCHAR(50)  | Descriptive product name (e.g., type, color, size).                            |
| `category_id`         | NVARCHAR(50)  | Identifier for the product's category.                                         |
| `category`            | NVARCHAR(50)  | Broad product classification (e.g., "Bikes", "Components").                    |
| `subcategory`         | NVARCHAR(50)  | Detailed classification within the category.                                   |
| `maintenance_required`| NVARCHAR(50)  | Indicates if maintenance is needed (e.g., "Yes", "No").                        |
| `cost`                | INT           | Product’s base price.                                                          |
| `product_line`        | NVARCHAR(50)  | Product line or series (e.g., "Road", "Mountain").                             |
| `start_date`          | DATE          | Date when the product became available.                                        |

---

### 3. `gold.fact_sales`

**Purpose:**  
Stores transactional sales data for analysis and reporting.

**Columns:**

| Column Name     | Data Type     | Description                                                                 |
|-----------------|---------------|-----------------------------------------------------------------------------|
| `order_number`  | NVARCHAR(50)  | Unique identifier for each sales order (e.g., "SO54496").                   |
| `product_key`   | INT           | Foreign key to the product dimension.                                       |
| `customer_key`  | INT           | Foreign key to the customer dimension.                                      |
| `order_date`    | DATE          | Date when the order was placed.                                             |
| `shipping_date` | DATE          | Date when the order was shipped.                                            |
| `due_date`      | DATE          | Payment due date for the order.                                             |
| `sales_amount`  | INT           | Total value of the sale in whole currency units.                            |
| `quantity`      | INT           | Number of units ordered.                                                    |
| `price`         | INT           | Price per unit in whole currency units.                                     |
