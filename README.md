# Dimentional-Modeling-
EZ Trade is a Business Intelligence (BI) dimensional data model designed to support analytical reporting, dashboards, and KPI tracking for a trading and sales platform.  The model follows dimensional modeling best practices popularized by Ralph Kimball, organizing data into fact tables and dimension tables.

# EZ Trade – Dimensional Data Model
Overview

EZ Trade is a Business Intelligence (BI) dimensional data model designed to support analytical reporting, dashboards, and KPI tracking for a trading and sales platform.

The model follows dimensional modeling best practices popularized by Ralph Kimball, organizing data into fact tables and dimension tables to enable fast, intuitive, and scalable analytics.

# This model is optimized for:

Sales and trading analysis

Time-based trend analysis

Customer and product performance reporting

Executive dashboards and BI tools

# Design Goals

Enable fast analytical queries

Support business-friendly reporting

Simplify joins for BI tools

Preserve historical context

Scale to large transactional volumes

# Modeling Approach

The EZ Trade data warehouse uses a Star Schema, where:

Fact tables store measurable business events

Dimension tables provide descriptive context

This approach prioritizes read performance and usability over strict normalization.

# Schema Overview
Central Fact Table

Fact_Trades

# Supporting Dimension Tables

Dim_Date

Dim_Customer

Dim_Product

Dim_Trader

Dim_Market

Dim_Order_Type

Fact Table
Fact_Trades

# Stores quantitative metrics related to each executed trade.

Grain:
One row per completed trade transaction.

Columns:

Trade_Key (Surrogate Key)

Date_Key (FK)

Customer_Key (FK)

Product_Key (FK)

Trader_Key (FK)

Market_Key (FK)

Order_Type_Key (FK)

Trade_Quantity

Trade_Price

Trade_Value

Commission_Amount

Profit_Loss

Measures:

Total Trade Value

Total Volume

Total Commission

Net Profit / Loss

Dimension Tables
Dim_Date

Provides time-based analysis.

Attributes:

Date

Day

Month

Quarter

Year

Fiscal_Year

Is_Weekend

Dim_Customer

Describes customers placing trades.

Attributes:

Customer_Name

Customer_Type

Region

Country

Account_Status

Dim_Product

Describes traded financial instruments.

Attributes:

Product_Name

Product_Type

Asset_Class

Sector

Currency

Dim_Trader

Describes internal traders or brokers.

Attributes:

Trader_Name

Desk

Experience_Level

Office_Location

Dim_Market

Describes trading venues or exchanges.

Attributes:

Market_Name

Market_Type

Country

Time_Zone

Dim_Order_Type

Describes how the trade was placed.

Attributes:

Order_Type (Market, Limit, Stop)

Execution_Method

Risk_Category

Slowly Changing Dimensions (SCD)

EZ Trade uses Slowly Changing Dimensions Type 2 where historical accuracy is required.

# Examples:

Customer region changes

Trader desk changes

Product classification updates

SCD Columns:

Effective_Start_Date

Effective_End_Date

Is_Current

# Why Dimensional Modeling?
Feature	Benefit
Star Schema	Simple joins and faster queries
Surrogate Keys	Stable historical tracking
Additive Facts	Accurate aggregation
Denormalized Dimensions	Business-friendly reporting
Example Analytical Queries

Total trade value by market and month

Profit/Loss by trader and quarter

Customer trading volume by region

Product performance by asset class

Commission trends over time

BI & Analytics Use Cases

# This model is designed to integrate seamlessly with:

Tableau

Power BI

Looker

Excel Pivot Tables

SQL-based reporting tools

Assumptions

Each trade represents a finalized transaction

Monetary values are stored in a single reporting currency

Time dimension is pre-populated

Historical changes must be preserved for auditability

Future Enhancements

Add Fact_Daily_Snapshot for daily KPIs

Add Risk Metrics Fact Table

Support real-time streaming ingestion

Add derived KPIs (Sharpe Ratio, Exposure)

# Conclusion

The EZ Trade Dimensional Model provides a robust, scalable, and business-friendly foundation for BI analytics.
It follows proven dimensional modeling principles and supports both operational insight and strategic decision-making.
