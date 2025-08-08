# Add Alerting to your report using Activator

This section provides steps to add alerts to report you created in previous section.

### Steps
1. Right click on the visual which you want to use for creating an alert. For this example, we will use the line graph that shows Profit by Buying Groups. We can see the Profit for "Tailspin toys" doesn't usually go over $15M. So, lets create an alert to be notified whenever it does go over $15M. Right click on the line graph corresponding to "Tailspin Toys" and click on "Add Alert"
![alt text](/PowerBI/images/Activator1.png)
2. Now, click on "My PowerBI Activator Alerts" at the bottom of the alert window
![alt text](/PowerBI/images/Activator4.png)
3. In the next window, make sure you choose your workspace and the name you want for your activator
![alt text](/PowerBI/images/Activator5.png)
4. Now, configure the alert. Select "Becomes", use condition = "Greater than", and for value use "15000000".
![alt text](/PowerBI/images/Activator2.png)
You can also rename the alert if you like and also open it in activator.
5. When prompted for selecting measure, choose the line graph
![alt text](/PowerBI/images/Activator3.png)
6. View in Activator, go to your workspace and click on "My PowerBI Activator Alerts"
![alt text](/PowerBI/images/Activator6.png)
you'll see something like below. 
![alt text](/PowerBI/images/Activator7.png)
To trigger the alert you can insert additional data into underlying tables such as that Tailspin Toys Profit grows over $15M. This is not part of the tutorial.