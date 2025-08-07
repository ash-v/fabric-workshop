## Financial Overview report
1. Overall Sales
2. Overall Profit
3. Total Items sold
4. Total Sales and Profit by Territory
5. Total Sales Profit by Customer Category
6. Total Sales by Buying Group
7. Daily Sales & Profit trend line
![alt text](/PowerBI/images/SampleReport.png)

### Steps
Assuming Gold Zone Lakehouse is already created and loaded with [sample data](https://learn.microsoft.com/en-us/sql/samples/wide-world-importers-what-is?view=sql-server-ver17).
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
4. Now, semantic model is ready. Let's create a report on this model by going to "File">"Create new report". This should take you to blank report
![alt text](/PowerBI/images/Reporting1.png)
5. Let's set background to light blue
![alt text](/PowerBI/images/Reporting2.png)
6. Add "Total Sales" on top left corner by 
    - expaning table "fact_Sales"
    - click column "TotalExcludingTax"
    - under "Visualization" tab, select visualization type "123"
    - Adjust the size of the box on top left of the report to your liking
![alt text](/PowerBI/images/Reporting3.png)
    - For rounded corners, select the tile > go to middle section of visualization tab > Effects > Visual Border > set Rounded Corners to 10
    ![alt text](/PowerBI/images/Reporting4.png)
7. Follow step 6 for visualizing profit tile using "Profit" column and total units sold tile using "Quantity" column. It should look like this
![alt text](/PowerBI/images/Reporting5.png)
8. Let's add "Total Sales and Profit by Territory"
    - Expand table "dimension_city" and select column "SalesTerritory"
    - Then, expand table "fact_Sales" and select columns "TotalExcludingTax" and "Profit"
    - Then, in visualization tab click on stacked horizontal bar charts
    you should see a stack bar chart as shown below
    ![alt text](/PowerBI/images/Reporting6.png)
    Continue following steps to format the image
    - select the bar chat and in visualization tab go to "X-axis" section. Click down arrow to open menu for each column "TotalExcludingTax" and "Profit" and select "Rename for this visual"
    ![alt text](/PowerBI/images/Reporting7.png)  
    - Rename "Sum of TotalExcludingTax" to "Sales" and "Sum of Profit" to "Profit"
    - Similarly, update Y-axis label to "Sales Territory"
    - Make the corners rounded as mentioned above
9. Add visual for "Total Sales and Profit by Customer Category"
    - Expand table "dimension_customer",Select column "Category"
    - Then, expand table "fact_Sales" and select columns "TotalExcludingTax" and "Profit"
    - Then, in visualization tab click on stacked vertical bar charts
    - Update label of Y-axis as described above to "Sales" and "Profit"
    - Make corners rounded as described above
    ![alt text](/PowerBI/images/Reporting8.png)