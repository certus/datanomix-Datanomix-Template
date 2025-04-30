# Data Model Documentation for Qlik Sense Script

## Overview
This document provides an overview of the data model that will be generated after executing the provided Qlik Sense load script. It includes information on tables, fields, keys, and relationships, as well as derived date fields using the `autoCalendar` feature.

---

## Tables and Relationships

### 1. Products
- **Fields**:
  - `ProductID`: Key field to link with the `Sales` table
  - `ProductName`: Name of the product
  - `Category`: Product main category
  - `SubCategory`: Subcategory within the main category
  - `UnitPrice`: Price per unit
  - `UnitCost`: Cost per unit

### 2. Customers
- **Fields**:
  - `CustomerID`: Key field to link with the `Sales` table
  - `CustomerName`: Name of the customer
  - `City`: Customer's city
  - `State`: Customer's state
  - `Country`: Customer's country
  - `CustomerSegment`: Segment to which the customer belongs

### 3. SalesReps
- **Fields**:
  - `SalesRepID`: Key field to link with the `Sales` and `Targets` tables
  - `SalesRepName`: Name of the sales representative
  - `Region`: Region of responsibility
  - `HireDate`: Date of employment

### 4. Sales
- **Fields**:
  - `SalesID`: Unique identifier for each sales transaction
  - `SalesDate`: The date of the sale
    - **Derived Fields**:
      - `SalesDate.autoCalendar.Year`
      - `SalesDate.autoCalendar.Quarter`
      - `SalesDate.autoCalendar.YearQuarter`
      - `SalesDate.autoCalendar.Month`
      - `SalesDate.autoCalendar.YearMonth`
      - `SalesDate.autoCalendar.Week`
      - `SalesDate.autoCalendar.Date`
      - `SalesDate.autoCalendar.InYTD`
      - `SalesDate.autoCalendar.YearsAgo`
      - `SalesDate.autoCalendar.InQTD`
      - `SalesDate.autoCalendar.QuartersAgo`
      - `SalesDate.autoCalendar.QuarterRelNo`
      - `SalesDate.autoCalendar.InMTD`
      - `SalesDate.autoCalendar.MonthsAgo`
      - `SalesDate.autoCalendar.MonthRelNo`
      - `SalesDate.autoCalendar.InWTD`
      - `SalesDate.autoCalendar.WeeksAgo`
      - `SalesDate.autoCalendar.WeekRelNo`
  - `CustomerID`: Foreign key linked to the `Customers` table
  - `ProductID`: Foreign key linked to the `Products` table
  - `SalesRepID`: Foreign key linked to the `SalesReps` and `Targets` tables
  - `Quantity`: Quantity of products sold
  - `SalesChannel`: The channel through which the sale was made
  - `PaymentMethod`: The form of payment used
  - `ShippingMethod`: The method of shipping used
  - `ProductPrice`: Price of the product at the time of the sale
  - `ProductCost`: Cost of the product
  - `SalesAmount`: Total sales amount, adjusted for various factors
  - `CostAmount`: Total cost amount, adjusted for various factors
  - `GrossProfit`: Profit from the sale
  - `GrossProfitMargin`: Margin of profit expressed as a percentage

### 5. Targets
- **Fields**:
  - `SalesRepID`: Foreign key linked to the `SalesReps` and `Sales` tables
  - `TargetMonth`: Monthly target date
  - `SalesTarget`: Sales target for the given month and sales representative

---

## Relationships between Tables
- **Sales and Customers**: Related via `CustomerID`.
- **Sales and Products**: Related via `ProductID`.
- **Sales and SalesReps**: Related via `SalesRepID`.
- **Targets and SalesReps**: Related via `SalesRepID`.
- **Sales and Targets**: Related via `SalesRepID`.

These relationships create a comprehensive sales data model that can be used to analyze sales performance across different products, customers, sales representatives, and time periods, taking into account regional, seasonal, and transactional characteristics.