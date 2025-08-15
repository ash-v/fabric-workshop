# Create a report in PowerBI

In this section we will create a PowerBI report using data provided in a Lakehouse. Details about the report to be created are below and exact steps with screenshots follow.

## Financial Overview report
1. Overall Sales
2. Overall Profit
3. Total Items sold
4. Total Sales and Profit by Territory
5. Total Sales Profit by Customer Category
6. Total Sales by Buying Group
7. Profit trend line by BuyingGroup
![alt text](/PowerBI/images/SampleReport.png)

### Steps
Assuming Gold Zone Lakehouse is already created and loaded with [sample data](https://learn.microsoft.com/en-us/sql/samples/wide-world-importers-what-is?view=sql-server-ver17).

1. Now, semantic model is ready. Let's create a report on this model. Please open the semantic model in your workspace.
![alt text](/PowerBI/images/SemanticModel6.png)
2. Once the semantic model console opens up, click on "Open semantic mode"
![alt text](/PowerBI/images/SemanticModel7.png)
3. On next screen, create a blank report by going to you "File">"Create new report". This should take you to blank report
![alt text](/PowerBI/images/Reporting1.png)
4. Let's set background to light blue
![alt text](/PowerBI/images/Reporting2.png)
5. Add "Total Sales" on top left corner by 
    - expaning table "fact_Sales"
    - click column "TotalExcludingTax"
    - under "Visualization" tab, select visualization type "123"
    - Adjust the size of the box on top left of the report to your liking
![alt text](/PowerBI/images/Reporting3.png)
    - For rounded corners, select the tile > go to middle section of visualization tab > Effects > Visual Border > set Rounded Corners to 10
    ![alt text](/PowerBI/images/Reporting4.png)
6. Follow step 6 for visualizing profit tile using "Profit" column and total units sold tile using "Quantity" column. It should look like this
![alt text](/PowerBI/images/Reporting5.png)
7. Let's add "Total Sales and Profit by Territory"
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
8. Add visual for "Total Sales and Profit by Customer Category"
    - Expand table "dimension_customer",Select column "Category"
    - Then, expand table "fact_Sales" and select columns "TotalExcludingTax" and "Profit"
    - Then, in visualization tab click on stacked vertical bar charts
    - Update label of Y-axis as described above to "Sales" and "Profit"
    - Make corners rounded as described above. It should look like below
    ![alt text](/PowerBI/images/Reporting8.png)
9. Add visual for "Total Sales by Buying Group"
    - From table "dimension_customer", select column "BuyingGroup"
    - Then, expand table "fact_Sales" and select columns "TotalExcludingTax"
    - In visualization tab, select donut chart
    - Rename Values from "Sum of TotalExcludingTax" to "Sales"
    - Make corner rounded. Should look like below
    ![alt text](/PowerBI/images/Reporting9.png)
10. Add visual for "Profit trend line by BuyingGroup"
    - From table "fact_Sales", select "invoiceDateKey" and "Profit"
    - From table "dimension_customer", select column "BuyingGroup"
    - Then, in visualization tab click on stacked line chart
    - Update Y-axis label to "Profit"
    - Make corners rounded. Should look like below
    ![alt text](/PowerBI/images/Reporting10.png)
    As you can see the line graph is not very clear. We will add a filter to show only Top 3 Buying Groups
    - Select the line graph, in Filters tab go to "BuyingGroup" and select "Top N" as filter type
    - Enter "3" as value for Top N. And, drag "Profit" from "fact_Sales" table in to "By Value" field. Hit "Apply filter". Now, you see it looks a bit better and shows only top 3 buying groups by Profit.
    ![alt text](/PowerBI/images/Reporting11.png)
    - Save the report, by clicking on "File" on top left corner and entering name of the report as "rp_PowerBI_Tutorial". Make sure you're saving in the folder corresponding to your name.
    ![alt text](/PowerBI/images/Reporting12.png)
    ![alt text](/PowerBI/images/Reporting13.png)

Next, you can go to [Activator tutorial](/PowerBI/workbooks/Activator.md)