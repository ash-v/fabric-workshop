# Copilot in PowerBI

This workbook walks through some of the ways to leverage copilot when working with PowerBI

### 1. Creating New report
 - go to your workspace, click on three dots next to you semantic model and select "Create report"
 ![alt text](/PowerBI/images/Copilot1.png)
 - When a blank report opens up, click on "copilot" and then "Get Started"
 ![alt text](/PowerBI/images/Copilot2.png)
 - Let's start with asking copilot for suggestion by clicking on "Suggest content for a new report page"
 ![alt text](/PowerBI/images/Copilot3.png)
 - Copilot suggest a few different options, let's hit "Create" on first one i.e. "Sales Overview"
 ![alt text](/PowerBI/images/Copilot4.png)
 - It creates a simple report
 ![alt text](/PowerBI/images/Copilot5.png)
 - Let's try to give it a full prompt as follows
```
Can you create a Financial Overview report that has following metrics?
1. Overall Sales
2. Overall Profit
3. Total Items sold
4. Total Sales and Profit by Territory
5. Total Sales Profit by Customer Category
6. Total Sales by Buying Group
```
should create something like below
![alt text](/PowerBI/images/Copilot6.png)

### 2. Updating existing visuals
 - In the last dashboard, let's try to update "Total Sales by Buying Group" to a donut chart with following prompt
```
In this report, can you convert "Total Sales By Buying Group" to a donut chart?
```
It should update the visual to something like below
![alt text](/PowerBI/images/Copilot7.png)

### 3. Chatting with your data
 - You can also ask copilot specific question about your data, when you ask questions you may have to turn on Q&A for Semantic model
 - Let's ask a question, notice in the screenshot copilot is asking me to switch on Q&A on this semantic model. All I need to do is click on the link it provided and I'm good to go
 ```
 Question : Which City in Southeast region is most Profitable?
 ```
 ![alt text](/PowerBI/images/Copilot8.png)

 **Note: Copilot might ask you to refresh the page. Make sure you save your report before refreshing the page**
 - Now, copilot answers the question and describes how it arrived at this answer so that you can verify it if you'd like.
 ![alt text](/PowerBI/images/Copilot9.png) 
 
 You can continue to ask more question. In general, it's better to start with "Question:" when asking a question versus requesting a visual

You can save the report, by clicking on "File" on top left corner and entering name of the report as "rp_PowerBICopilot_Tutorial". Make sure you're saving in the folder corresponding to your name.