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

## Data Model

The dataset follows a star schema design with the following relationships:

- Transactions are linked to Products, Customers, Stores, and Calendar
- Stores are linked to Regions
- Returns are linked to Products and Calendar

## Key Metrics

The dataset allows for analysis of:
- Sales performance by product, store, region, and time period
- Customer purchasing patterns and segmentation
- Return rates and reasons
- Regional performance comparisons
- Store performance metrics

## Usage

This dataset is ideal for:
- Sales analysis and forecasting
- Customer behavior analysis
- Inventory management
- Regional performance analysis
- Store performance optimization
- Return analysis and reduction strategies

## Data Quality

The dataset has been cleaned and structured for analysis, with:
- Consistent date formatting
- Standardized product categories
- Normalized customer segments
- Hierarchical regional structure
- Complete transaction history

## File Sizes
- Products: ~102KB
- Customers: ~1.5MB
- Returns: ~138KB
- Stores: ~2.8KB
- Regions: ~2.8KB
- Calendar: ~7.8KB
- Transactions 1997: ~2.9MB
- Transactions 1998: ~6.1MB 