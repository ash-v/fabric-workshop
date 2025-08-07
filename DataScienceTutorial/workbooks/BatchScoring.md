# Perform batch scoring and save predictions to a lakehouse

This tutorial shows how to import the registered LightGBMClassifier model that you built in part 3. That tutorial used the Microsoft Fabric MLflow model registry to train the model, and then perform batch predictions on a test dataset loaded from a lakehouse.

With Microsoft Fabric, you can operationalize machine learning models with the scalable PREDICT function. That function supports batch scoring in any compute engine. You can generate batch predictions directly from a Microsoft Fabric notebook, or from the item page of a given model. For more information about the PREDICT function, visit this resource.

To generate batch predictions on the test dataset, use version 1 of the trained LightGBM model. That version showed the best performance among all trained machine learning models. You load the test dataset into a spark DataFrame, and create an MLFlowTransformer object to generate batch predictions. You can then invoke the PREDICT function using one of these techniques:

Transformer API from SynapseML
Spark SQL API
PySpark user-defined function (UDF)

1. Create a new notebook and name it "BatchScoringAndPredictions"
![alt text](/DataScienceTutorial/images/ExploreAndCleanData1.png)
2. Attach Lakehouse to Notebook by clicking on "Add data items" on left pane of the screen and then selecting "Existing Data Sources"
![alt text](/DataScienceTutorial/images/ExploreAndCleanData3.png)
3. Load the test data
```
df_test = spark.read.format("delta").load("Tables/dbo/df_test")
display(df_test)

```
4. PREDICT with the Transformer API
To use the Transformer API from SynapseML, you must first create an MLFlowTransformer object.   

Instantiate MLFlowTransformer object - The MLFlowTransformer object serves as a wrapper around the MLFlow model that you registered in Part 3. It allows you to generate batch predictions on a given DataFrame. To instantiate the MLFlowTransformer object, you must provide the following parameters:
- The test DataFrame columns that the model needs as input (in this case, the model needs all of them)
- A name for the new output column (in this case, predictions)
- The correct model name and model version to generate the predictions (in this case, lgbm_sm and version 1)
Install compatible version of scikit learn.
```
%pip install scikit-learn==1.6.1
```
```
from synapse.ml.predict import MLFlowTransformer

model = MLFlowTransformer(
    inputCols=list(df_test.columns),
    outputCol='predictions',
    modelName='lgbm_sm',
    modelVersion=1
)
```
Now that you have the MLFlowTransformer object, you can use it to generate batch predictions, as shown in the following code snippet:
```
import pandas

predictions = model.transform(df_test)
display(predictions)
```
5. PREDICT with the Spark SQL API
```
from pyspark.ml.feature import SQLTransformer 

# Substitute "model_name", "model_version", and "features" below with values for your own model name, model version, and feature columns
model_name = 'lgbm_sm'
model_version = 1
features = df_test.columns

sqlt = SQLTransformer().setStatement( 
    f"SELECT PREDICT('{model_name}/{model_version}', {','.join(features)}) as predictions FROM __THIS__")

# Substitute "X_test" below with your own test dataset
display(sqlt.transform(df_test))
```
6. PREDICT with a user-defined function (UDF)
```
from pyspark.sql.functions import col, pandas_udf, udf, lit

# Substitute "model" and "features" below with values for your own model name and feature columns
my_udf = model.to_udf()
features = df_test.columns

display(df_test.withColumn("predictions", my_udf(*[col(f) for f in features])))
```
7. Write model prediction results to the lakehouse
```
# Save predictions to lakehouse to be used for generating a Power BI report
table_name = "customer_churn_test_predictions"
predictions.write.format('delta').mode("overwrite").save(f"Tables/dbo/{table_name}")
print(f"Spark DataFrame saved to delta table: {table_name}")
```

Next, you can visualize your data with [PowerBI](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-data-science-create-report).