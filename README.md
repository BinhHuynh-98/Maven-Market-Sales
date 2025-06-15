# Maven Market Dataset

This repository contains a comprehensive retail dataset for Maven Market, a fictional retail chain. The dataset includes various aspects of the business operations from 1997-1998.

## Dataset Overview

The dataset consists of the following files:

### Core Data Files
- `MavenMarket_Products.csv` - Product catalog information
- `MavenMarket_Customers.csv` - Customer demographic and segmentation data
- `MavenMarket_Stores.csv` - Store location and information
- `MavenMarket_Regions.csv` - Regional hierarchy and management structure
- `MavenMarket_Calendar.csv` - Date dimension with fiscal calendar information

### Transaction Data
- `MavenMarket_Transactions_1997.csv` - Sales transactions for 1997
- `MavenMarket_Transactions_1998.csv` - Sales transactions for 1998
- `MavenMarket_Returns_1997-1998.csv` - Product returns data for 1997-1998

## DAX Measures

Total Sales = 
SUMX(
    'MavenMarket_Transactions',
    'MavenMarket_Transactions'[Quantity] * 'MavenMarket_Transactions'[Unit Price]
)

// Year-over-Year Sales Growth
YoY Sales Growth = 
VAR CurrentYearSales = [Total Sales]
VAR PreviousYearSales = 
    CALCULATE(
        [Total Sales],
        DATEADD('MavenMarket_Calendar'[Date], -1, YEAR)
    )
RETURN
    DIVIDE(
        CurrentYearSales - PreviousYearSales,
        PreviousYearSales,
        0
    )

// Average Transaction Value
Average Transaction Value = 
DIVIDE(
    [Total Sales],
    DISTINCTCOUNT('MavenMarket_Transactions'[Transaction ID]),
    0
)

// Return Rate
Return Rate = 
DIVIDE(
    COUNTROWS('MavenMarket_Returns'),
    COUNTROWS('MavenMarket_Transactions'),
    0
)

// Product Performance
Product Sales = 
CALCULATE(
    [Total Sales],
    ALLSELECTED('MavenMarket_Products')
)

// Store Performance
Store Sales = 
CALCULATE(
    [Total Sales],
    ALLSELECTED('MavenMarket_Stores')
)

// Regional Performance
Regional Sales = 
CALCULATE(
    [Total Sales],
    ALLSELECTED('MavenMarket_Regions')
)

// Customer Segment Analysis
Segment Sales = 
CALCULATE(
    [Total Sales],
    ALLSELECTED('MavenMarket_Customers'[Customer Segment])
)

// Time Intelligence
MTD Sales = 
CALCULATE(
    [Total Sales],
    DATESMTD('MavenMarket_Calendar'[Date])
)

YTD Sales = 
CALCULATE(
    [Total Sales],
    DATESYTD('MavenMarket_Calendar'[Date])
)

// Product Category Analysis
Category Sales = 
CALCULATE(
    [Total Sales],
    ALLSELECTED('MavenMarket_Products'[Product Category])
)

// Profit Margin
Profit Margin = 
DIVIDE(
    [Total Sales] - SUM('MavenMarket_Transactions'[Cost]),
    [Total Sales],
    0
)

// Customer Retention
Returning Customers = 
CALCULATE(
    DISTINCTCOUNT('MavenMarket_Customers'[Customer ID]),
    FILTER(
        'MavenMarket_Transactions',
        COUNTROWS('MavenMarket_Transactions') > 1
    )
)

// Store Traffic
Store Traffic = 
DISTINCTCOUNT('MavenMarket_Transactions'[Transaction ID])

// Product Return Rate by Category
Category Return Rate = 
DIVIDE(
    CALCULATE(
        COUNTROWS('MavenMarket_Returns'),
        ALLSELECTED('MavenMarket_Products'[Product Category])
    ),
    CALCULATE(
        COUNTROWS('MavenMarket_Transactions'),
        ALLSELECTED('MavenMarket_Products'[Product Category])
    ),
    0
)

// Seasonal Analysis
Seasonal Sales = 
CALCULATE(
    [Total Sales],
    ALLSELECTED('MavenMarket_Calendar'[Season])
)

// Regional Growth
Regional Growth = 
VAR CurrentRegionSales = [Regional Sales]
VAR PreviousRegionSales = 
    CALCULATE(
        [Regional Sales],
        DATEADD('MavenMarket_Calendar'[Date], -1, YEAR)
    )
RETURN
    DIVIDE(
        CurrentRegionSales - PreviousRegionSales,
        PreviousRegionSales,
        0
    ) 
