# Exploration

This section covers two key ways of exploring your data.
- [Using DAX Queries](#a-using-dax-queries)
- [Using Fabric Exploration item](#b-using-fabric-exploration-items)

You should have a semantic model already created for you in your workspace. All workshop atttendees will read from the same semantic model provded by the IT team.


## A. Using DAX queries
1. Go to your workspace and click on semantic model
![alt text](/PowerBI/images/Exploration1.png)
2. Once semantic model console opens up, click on "Write DAX Query"
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
    - In case, "Package" shows up as Coluns and not as rows. You should drag and drop "package" column under 
    ![alt text](/PowerBI/images/Exploration8.png)
    - From "Drill", ensure "Drill up" selected
    - From "Sort", ensure sort axis is "Sum of Profit"
    Should look like below
    ![alt text](/PowerBI/images/Exploration6.png)
    - Now, click on one of th bars to drill down to package level. If clicking doesn't work, you can right-click on the bars and hit "drill down" to see package level details at the selected Sales Territory
    ![alt text](/PowerBI/images/Exploration7.png)

You can continue to explore and learn more about the data. You can also save and share such visual explorations with your colleagues. This is not covered in this tutorial.

Next, you can go to [Report creation tutorial](/PowerBI/workbooks/PowerBIManualReport.md)