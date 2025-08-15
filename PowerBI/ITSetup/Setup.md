# Workshop setup

This workshop requires some setup to be completed by IT. Workshop attendees can assume that data is available in a Lakehouse and a Semantic Model is already created. Theses steps need to be completed by the IT team.

## Lakehouse setup
1. Go to your workspace, click "+ New item", type "Lakehouse", and click ing on Lakehouse tile
![alt text](/PowerBI/images/Setup1.png)
2. Name the lakehouse "lh_datastore" ![alt text](/PowerBI/images/Setup2.png)
3. This creates the lakehouse. Now, add sample data to the lakehouse by clicking on "Start with sample data".
![alt text](/PowerBI/images/Setup3.png)
4. Next screen, select "Retail Data Model from Wide World Importers"
![alt text](/PowerBI/images/Setup4.png)
This creates data. Now, let's create a semantic model.

## Semantic Model setup

1. Go to Lakehouse "lh_gold_zone" click on "New Semantic Model" 
![alt text](/PowerBI/images/SemanticModel1.png)
2. On the pop-up window, fill in the name of semantic model as "sm_powerbi_tutorial". Select tables as shown in the screenshot below.. and hit "Confirm"
![alt text](/PowerBI/images/SemanticModel2.png)
3. When Semantic Model opens up, make following connection by dragging and dropping
 - 3.1 Connect fact_sales table to dimentions_city on city_key by pressing down city_key on dimensions_city table and dragging to over to city_key column on fact_Sales_table. 
 ![alt text](/PowerBI/images/SemanticModel3.png)
 Following screen will appear when you do this... hit "Save"
 ![alt text](/PowerBI/images/SemanticModel4.png)
 - 3.2 Similarly, connect fact_Sales table with dimensions_customer
 ![alt text](/PowerBI/images/SemanticModel5.png)


