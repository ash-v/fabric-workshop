# Exploration

This section covers two key ways of exploring your data.
- [Using DAX Queries](#a-using-dax-queries)
- [Using Fabric Exploration item](#b-using-fabric-exploration-items)

But first we need to create a semantic model. Let's start

## Create Semantic Model
1. Go to Lakehouse "lh_gold_zone" click on "New Semantic Model" 
![alt text](/PowerBI/images/SemanticModel1.png)
2. On the pop-up window, fill in the name of semantic model as "sm_powerbi_tutorial". Select tables as shown in the screenshot below.. and hit "Confirm"
![alt text](image.png)
3. When Semantic Model opens up, make following connection by dragging and dropping
 - 3.1 Connect fact_sales table to dimentions_city on city_key by pressing down city_key on dimensions_city table and dragging to over to city_key column on fact_Sales_table. 
 ![alt text](/PowerBI/images/SemanticModel3.png)
 Following screen will appear when you do this... hit "Save"
 ![alt text](/PowerBI/images/SemanticModel4.png)
 - 3.2 Similarly, connect fact_Sales table with dimensions_customer
 ![alt text](/PowerBI/images/SemanticModel5.png)


## A. Using DAX queries
1. Go to your workspace and click on semantic model
![alt text](/PowerBI/images/Exploration1.png)
2. Once semantic model opens up, click on "Write DAX Query"
![alt text](/PowerBI/images/Exploration2.png)
3. Explore data using DAX queries
- 3.1 Explore 'fact_sale' table
```
EVALUATE
    TOPN(100, 'fact_sale')
```
![alt text](/PowerBI/images/Exploration3.png)


- 3.2 : Next we have a DAX query that is useful for creating a detailed sales report that combines sales data with related city and customer information.
    
    You might use this query to analyze each sale with context about where it happened (city, state, country) and who made the purchase (customer, customer category). 

```
    EVALUATE
  SELECTCOLUMNS(
    ADDCOLUMNS(
      'fact_sale',
      "City", RELATED('dimension_city'[City]),
      "StateProvince", RELATED('dimension_city'[StateProvince]),
      "Country", RELATED('dimension_city'[Country]),
      "Customer", RELATED('dimension_customer'[Customer]),
      "CustomerCategory", RELATED('dimension_customer'[Category])
    ),
    "SaleKey", [SaleKey],
    "InvoiceDate", [InvoiceDateKey],
    "City", [City],
    "StateProvince", [StateProvince],
    "Country", [Country],
    "Customer", [Customer],
    "CustomerCategory", [CustomerCategory],
    "Quantity", [Quantity],
    "UnitPrice", [UnitPrice],
    "TotalIncludingTax", [TotalIncludingTax]
  )
ORDER BY
  [SaleKey] ASC

```

## B. Using Fabric "Exploration" items
1. Go to your workspace and create a "+ New Item". 
![alt text](/PowerBI/images/Exploration4.png)
2. Select "Exploration", on next window select you semantic model and click "Explore"
![alt text](/PowerBI/images/Exploration5.png)
3. Start exploring
    - From table "dimension_city", select column "SalesTerritory"
    - From table "fact_sale", select columns "TotalExcludingTax", "Profit", and "Package"
    - From "Visual", select stacked bar graphs
    - From "Drill", ensure "Drill up" selected
    - From "Sort", ensure sort axis is "Sum of Profit"
    Should look like below
    ![alt text](/PowerBI/images/Exploration6.png)
    - Now, click on one of th bars to drill down to package level
    ![alt text](/PowerBI/images/Exploration7.png)

You can continue to explore and learn more about the data. You can also save and share such visual explorations with your colleagues. This is not covered in this tutorial.

Next, you can go to [Report creation tutorial](/PowerBI/workbooks/PowerBIManualReport.md)