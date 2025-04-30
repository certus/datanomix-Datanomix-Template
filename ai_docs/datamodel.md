# Data Model Documentation

This document describes the data model created by the Qlik Sense load script. It consists of the main entities: Products, Customers, Sales Reps, Sales, and Targets, along with relationships and derived fields.

## Tables

### 1. Products

- **Fields:**
  - `ProductID`: Unique identifier for each product.
  - `ProductName`: Name of the product.
  - `Category`: High-level classification of the product.
  - `SubCategory`: More specific classification.
  - `UnitPrice`: Retail price of the product.
  - `UnitCost`: Cost price of the product.

- **Primary Key:** `ProductID`

### 2. Customers

- **Fields:**
  - `CustomerID`: Unique identifier for each customer.
  - `CustomerName`: Name of the customer.
  - `City`: City where the customer is located.
  - `State`: State where the customer is located.
  - `Country`: Country where the customer is located.
  - `CustomerSegment`: Segment category of the customer (e.g., Corporate, Small Business, Consumer).

- **Primary Key:** `CustomerID`

### 3. Sales Reps

- **Fields:**
  - `SalesRepID`: Unique identifier for each sales representative.
  - `SalesRepName`: Name of the sales representative.
  - `Region`: Geographical region managed by the sales representative.
  - `HireDate`: Date when the sales representative was hired.

- **Primary Key:** `SalesRepID`

### 4. Sales

- **Fields:**
  - `SalesID`: Unique identifier for each sales transaction.
  - `SalesDate`: Date of the sales transaction.
  - `CustomerID`: Identifier for the customer associated with the sale.
  - `ProductID`: Identifier for the product sold.
  - `SalesRepID`: Identifier for the sales representative handling the transaction.
  - `Quantity`: Number of products sold in the transaction.
  - `SalesChannel`: Method of sale (e.g., Online, In-Store, Phone).
  - `PaymentMethod`: Method of payment used (e.g., Credit Card, Cash).
  - `ShippingMethod`: Method of shipping chosen for the transaction.
  - `ProductPrice`: Price per unit of product.
  - `ProductCost`: Cost per unit of product.
  - `SalesAmount`: Total sales value (adjusted) of the transaction.
  - `CostAmount`: Total cost value (adjusted) of the transaction.
  - `GrossProfit`: Total gross profit from the transaction.
  - `GrossProfitMargin`: Gross profit margin as a percentage.

- **Keys:** 
  - `CustomerID` (foreign key, relates to Customers)
  - `ProductID` (foreign key, relates to Products)
  - `SalesRepID` (foreign key, relates to Sales Reps)

- **Derived Fields (AutoCalendar for `SalesDate`):**
  - `SalesDate.autoCalendar.Year`
  - `SalesDate.autoCalendar.Quarter`
  - `SalesDate.autoCalendar.YearQuarter`
  - `SalesDate.autoCalendar.Month`
  - `SalesDate.autoCalendar.YearMonth`
  - `SalesDate.autoCalendar.Week`
  - `SalesDate.autoCalendar.Date`
  - Additional temporal fields for analytics, such as `SalesDate.autoCalendar.InYTD`, `SalesDate.autoCalendar.MonthsAgo`, etc.

### 5. Targets

- **Fields:**
  - `SalesRepID`: Identifier for the sales representative.
  - `TargetMonth`: Date representing the month the target is applicable to.
  - `SalesTarget`: Sales target for the representative in the given month.

- **Keys:**
  - `SalesRepID` (foreign key, relates to Sales Reps)

## Relationships

- **Products and Sales:** Linked through `ProductID`.
- **Customers and Sales:** Linked through `CustomerID`.
- **Sales Reps and Sales:** Linked through `SalesRepID`.
- **Sales Reps and Targets:** Linked through `SalesRepID`.

This data model facilitates analysis of sales performance across different dimensions, such as time (via autoCalendar), products, customers, and sales representatives. It also includes metrics to evaluate sales growth patterns and target achievement.