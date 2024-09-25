# Lab 01: Train and track machine learning models with MLflow in Microsoft Fabric

**Introduction**

In this Use case, you’ll train a machine learning model to predict a
quantitative measure of diabetes. You’ll train a regression model with
scikit-learn, and track and compare your models with MLflow.By
completing this lab, you’ll gain hands-on experience in machine learning
and model tracking, and learn how to work
with *notebooks*, *experiments*, and *models* in Microsoft Fabric.

**Objectives**

- To create Fabric workspace with trial enabled.

- To set up "TrainModel_Lakehouse" and upload data.

- To create a notebook for interactive coding.

- To load data into Pandas and Spark DataFrames.

- To train Logistic Regression and Decision Tree models, track with
  MLflow.

- To manage experiments using MLflow: list, retrieve, and order runs.

- To explore experiment results in Microsoft Fabric.

- To save best model as "model-churn" in Registered versions.

- To rename and save the notebook, end Spark session.

- To delete the created workspace in Microsoft Fabric.

## Task 0: Sync Host environment time 

1.  In your VM, navigate and click in the **Search bar**, type
    **Settings** and then click on **Settings** under **Best match**.  

<img src="./media/image1.png" style="width:6.5in;height:5.58056in"
alt="A screenshot of a computer Description automatically generated" /> 

2.  On Settings window, navigate and click on **Time & language**. 

<img src="./media/image2.png" style="width:6.5in;height:5.71667in"
alt="A screenshot of a computer Description automatically generated" /> 

3.  On **Time & language** page, navigate and click on **Date & time**. 

<img src="./media/image3.png" style="width:6.5in;height:5.27153in"
alt="A screenshot of a computer Description automatically generated" /> 

4.  Scroll down and navigate to **Additional settings** section, then
    click on **Syn now** button. It will take 3-5 minutes to syn. 

<img src="./media/image4.png" style="width:6.5in;height:5.04375in"
alt="A screenshot of a computer Description automatically generated" /> 

5.  Close the **Settings** window.  

<img src="./media/image5.png" style="width:6.5in;height:5.11736in"
alt="A screenshot of a computer Description automatically generated" />

## Task 1: Sign in to Power BI account and sign up for the free [Microsoft Fabric trial](https://learn.microsoft.com/en-us/fabric/get-started/fabric-trial)

1.  Open your browser, navigate to the address bar, and type or paste
    the following URL:
    [https://app.fabric.microsoft.com/](https://app.fabric.microsoft.com/,)
    then press the **Enter** button.

> <img src="./media/image6.png" style="width:6.5in;height:2.89653in"
> alt="A search engine window with a red box Description automatically generated with medium confidence" />

2.  In the **Microsoft Fabric** window, enter your given credentials,
    and click on the **Submit** button.

> <img src="./media/image7.png" style="width:6.49167in;height:3.11667in"
> alt="A close up of a white and green object Description automatically generated" />

3.  Then, In the **Microsoft** window enter the password and click on
    the **Sign in** button**.**

> <img src="./media/image8.png" style="width:4.50833in;height:3.83333in"
> alt="A login screen with a red box and blue text Description automatically generated" />

4.  In **Stay signed in?** window, click on the **Yes** button.

> <img src="./media/image9.png" style="width:4.58333in;height:3.66667in"
> alt="A screenshot of a computer error Description automatically generated" />

5.  You’ll be directed to Power BI Home page.

<img src="./media/image10.png" style="width:7.17276in;height:3.31357in"
alt="A screenshot of a computer Description automatically generated" />

6.  On **Power BI Home** page, click on the **Account manager** on the
    right side. In the Account manager blade, navigate and
    select **Start trial as shown in the below image.**

<img src="./media/image11.png" style="width:7.22864in;height:1.92083in"
alt="A screenshot of a computer Description automatically generated" />

7.  If prompted, agree to the terms and then select **Start trial**.

> <img src="./media/image12.png" style="width:6.5in;height:1.64167in"
> alt="A screenshot of a computer Description automatically generated" />

8.  Once your trial capacity is ready, you receive a confirmation
    message. Select **Fabric Home Page** to begin working in Fabric.

> <img src="./media/image13.png" style="width:5.54167in;height:2.01667in"
> alt="A screenshot of a computer Description automatically generated" />

9.  Open your Account manager again. Notice that you now have a heading
    for **Trial status**. Your Account manager keeps track of the number
    of days remaining in your trial. You will also see the countdown in
    your Fabric menu bar when you work in a product experience.

> <img src="./media/image14.png" style="width:6.5in;height:3.80833in"
> alt="A screenshot of a computer Description automatically generated" />

## Task 2: Create a workspace

Before working with data in Fabric, create a workspace with the Fabric
trial enabled.

1.  In the **Microsoft Fabric** home page, select the **Power BI**
    template.

> <img src="./media/image15.png" style="width:6.49167in;height:4.20833in"
> alt="A screenshot of a computer Description automatically generated" />

2.  In the **Power BI Home** page menu bar on the left,
    select **Workspaces** (the icon looks similar to 🗇).

> <img src="./media/image16.png" style="width:6.5in;height:6.23333in"
> alt="A screenshot of a computer Description automatically generated" />

3.  In the Workspaces pane Select **+** **New workspace**.

> <img src="./media/image17.png" style="width:4.04583in;height:7.50692in"
> alt="A screenshot of a computer Description automatically generated" />

4.  In the **Create a workspace tab**, enter the following details and
    click on the **Apply** button.

| **Name** | ***TrainModel_FabricXX** (*XX can be a unique number) (here, we entered **TrainModel_Fabric29*)*** |
|----|----|
| **Advanced** | Under **License mode**, select **Trial** |
| **Default storage format** | **Small dataset storage format** |

> <img src="./media/image18.png" style="width:4.80213in;height:5.65341in"
> alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image19.png" style="width:5.25417in;height:6.23887in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image20.png" style="width:3.47485in;height:4.24432in"
alt="A screenshot of a computer Description automatically generated" />

5.  Wait for the deployment to complete. It takes 2-3 minutes to
    complete. When your new workspace opens, it should be empty.

## Task 3: Create a lakehouse and upload files

Now that you have a workspace, it’s time to switch to the *Data
science* experience in the portal and create a data lakehouse for the
data files you’re going to analyze.

1.  At the bottom left of the Power BI portal, select the **Power
    BI** icon and switch to the **Data Engineering** experience.

> <img src="./media/image21.png"
> style="width:4.25833in;height:7.49167in" />

2.  In the **Synapse** **Data engineering** **Home** page, select
    **Lakehouse** under **New** pane.

> <img src="./media/image22.png" style="width:6.48333in;height:3.58333in"
> alt="A screenshot of a computer Description automatically generated" />

3.  In the **New lakehouse** dialog box, enter
    +++**TrainModel_Lakehouse+++** in the **Name** field, click on the
    **Create** button.

<img src="./media/image23.png" style="width:3.075in;height:1.875in"
alt="A screenshot of a computer Description automatically generated" />

4.  A new empty lakehouse will be created. You need to ingest some data
    into the **TrainModel_Lakehouse** for analysis.

<img src="./media/image24.png" style="width:6.5in;height:4.42083in"
alt="A screenshot of a computer Description automatically generated" />

5.  Wait for few minutes, you’ll will receive a notification stating -
    **Successfully created SQL endpoint**.

> <img src="./media/image25.png" style="width:4.29204in;height:2.35854in"
> alt="A screenshot of a computer Description automatically generated" />

## Task 4: Create a notebook

To train a model, you can create a *notebook*. Notebooks provide an
interactive environment in which you can write and run code (in multiple
languages) as *experiments*.

1.  At the bottom left of the TrainModel_Lakehouse page, select
    the **Data engineering** icon and switch to the **Data
    science** experience.

> <img src="./media/image26.png" style="width:4.425in;height:7.56667in" />

2.  In the **Synapse Data Science** **Home** page, select
    **Notebook**under current workspace of **TrainModel_FabricXX.**

<img src="./media/image27.png"
style="width:7.29745in;height:2.67917in" />

3.  After a few seconds, a new notebook containing a single *cell* will
    open. Notebooks are made up of one or more cells that can
    contain **code** or **markdown** (formatted text).

> <img src="./media/image28.png" style="width:7.01934in;height:4.36534in"
> alt="A screenshot of a computer Description automatically generated" />

4.  Select the first cell (which is currently a *code* cell), and then
    in the dynamic tool bar at its top-right, use the **M↓** button to
    convert the cell to a *markdown* cell.

<img src="./media/image29.png" style="width:7.3542in;height:1.63068in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image30.png" style="width:7.35296in;height:3.06845in"
alt="A screenshot of a computer Description automatically generated" />

When the cell changes to a markdown cell, the text it contains is
rendered.

5.  Use the **🖉 (Edit**) button to switch the cell to editing mode, then
    delete the content and enter the following text:

> +++# Train a machine learning model and track with MLflow+++

<img src="./media/image31.png" style="width:7.09475in;height:1.98674in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image32.png" style="width:7.44134in;height:2.57982in"
alt="A screenshot of a computer Description automatically generated" />

## Task 5: Load data into a dataframe

Now you’re ready to run code to get data and train a model. You’ll work
with the [diabetes
dataset](https://learn.microsoft.com/azure/open-datasets/dataset-diabetes?tabs=azureml-opendatasets?azure-portal=true) from
the Azure Open Datasets. After loading the data, you’ll convert the data
to a Pandas dataframe: a common structure for working with data in rows
and columns.

1.  In the **Lakehouse explorer** section, select Lakehouses and click
    on the **Add** button under the **Add lakehouse** to add a
    lakehouse.

> <img src="./media/image33.png" style="width:6.49167in;height:4.75in" />
>
> <img src="./media/image34.png" style="width:5.91099in;height:4.58704in"
> alt="A screenshot of a computer Description automatically generated" />

2.  In **Add lakehouse** dialog box, select **Existing lakehouse** radio
    button and select **Add**.

> <img src="./media/image35.png" style="width:3.48472in;height:2.18194in"
> alt="A screenshot of a computer Description automatically generated" />

3.  In **Choose the data you want to connect** page, select your
    lakehouse i.e., **TrainModel**\_**Lakehouse**, then click on the
    **Add** button.

<img src="./media/image36.png" style="width:7.35795in;height:4.20803in"
alt="A screenshot of a computer Description automatically generated" />

4.  In your notebook, use the **+ Code** icon below the latest cell
    output to add a new code cell to the notebook.

> **Tip**: To see the **+ Code** icon, move the mouse to just below and
> to the left of the output from the current cell. Alternatively, in the
> menu bar, on the **Edit** tab, select **+ Add code cell**.

5.  Enter the following code in it:

> +++# Azure storage access info for open dataset diabetes
>
> blob_account_name = "azureopendatastorage"
>
> blob_container_name = "mlsamples"
>
> blob_relative_path = "diabetes"
>
> blob_sas_token = r"" \# Blank since container is Anonymous access
>
> \# Set Spark config to access blob storage
>
> wasbs_path = f"wasbs://%s@%s.blob.core.windows.net/%s" %
> (blob_container_name, blob_account_name, blob_relative_path)
>
> spark.conf.set("fs.azure.sas.%s.%s.blob.core.windows.net" %
> (blob_container_name, blob_account_name), blob_sas_token)
>
> print("Remote blob path: " + wasbs_path)
>
> \# Spark read parquet, note that it won't load any data yet by now
>
> df = spark.read.parquet(wasbs_path)+++
>
> <img src="./media/image37.png" style="width:6.5in;height:2.91667in" />

6.  Use the **▷ Run cell** button on the left of the cell to run it.
    Alternatively, you can press **SHIFT** + **ENTER** on your keyboard
    to run a cell.

<img src="./media/image38.png"
style="width:7.37609in;height:3.2625in" />

> **Note**: Since this is the first time you’ve run any Spark code in
> this session, the Spark pool must be started. This means that the
> first run in the session can take a minute or so to complete.
> Subsequent runs will be quicker.

7.  Use the **+ Code** icon below the cell output to add a new code cell
    to the notebook, and enter the following code in it. Use the **▷ Run
    cell** button on the left of the cell to run it

> codeCopy
>
> +++display(df)+++

8.  When the cell command has completed, review the output below the
    cell, which should look similar to this:

<img src="./media/image39.png"
style="width:7.32374in;height:4.07083in" />

> The output shows the rows and columns of the diabetes dataset

9.  The data is loaded as a Spark dataframe. Scikit-learn will expect
    the input dataset to be a Pandas dataframe. Run the code below to
    convert your dataset to a Pandas dataframe:

> +++import pandas as pd
>
> df = df.toPandas()
>
> df.head()+++
>
> <img src="./media/image40.png"
> style="width:6.49167in;height:5.08333in" />

## Task 6: Train a machine learning model

Now that you’ve loaded the data, you can use it to train a machine
learning model and predict customer churn. You’ll train a model using
the Scikit-Learn library and track the model with MLflow.

1.  Hover your mouse below the output cell, you’ll see the **+
    Code** icon. Click on the **+ Code** icon and enter the following
    code in the cell. Use the **▷ Run cell** button on the left of the
    cell to run it

+++from sklearn.model_selection import train_test_split

X, y =
df\[\['AGE','SEX','BMI','BP','S1','S2','S3','S4','S5','S6'\]\].values,
df\['Y'\].values

X_train, X_test, y_train, y_test = train_test_split(X, y,
test_size=0.30, random_state=0)+++

<img src="./media/image41.png"
style="width:7.04893in;height:3.37083in" />

2.  Add another new code cell to the notebook, enter the following code
    in it, and run it:

> import mlflow
>
> experiment_name = "experiment-diabetes"
>
> mlflow.set_experiment(experiment_name)

<img src="./media/image42.png"
style="width:7.14868in;height:3.0375in" />

The code creates an MLflow experiment named **experiment-diabetes**.
Your models will be tracked in this experiment.

3.  Add another new code cell to the notebook, enter the following code
    in it, and run it.

> +++from sklearn.linear_model import LinearRegression
>
> with mlflow.start_run():
>
> mlflow.autolog()
>
> model = LinearRegression()
>
> model.fit(X_train, y_train)
>
> mlflow.log_param("estimator", "LinearRegression")+++

<img src="./media/image43.png"
style="width:7.24375in;height:3.8125in" />

The code trains a regression model using Linear Regression. Parameters,
metrics, and artifacts, are automatically logged with MLflow.
Additionally, you’re logging a parameter called **estimator** with the
value *LinearRegression*.

4.  Add another new code cell to the notebook, enter the following code
    in it, and run it.

> +++from sklearn.tree import DecisionTreeRegressor
>
> with mlflow.start_run():
>
> mlflow.autolog()
>
> model = DecisionTreeRegressor(max_depth=5)
>
> model.fit(X_train, y_train)
>
> mlflow.log_param("estimator", "DecisionTreeRegressor")+++

<img src="./media/image44.png"
style="width:7.3437in;height:3.77083in" />

The code trains a regression model using Decision Tree Regressor.
Parameters, metrics, and artifacts, are automatically logged with
MLflow. Additionally, you’re logging a parameter
called **estimator** with the value *DecisionTreeRegressor*.

## Task 7:Use MLflow to search and view your experiments

When you’ve trained and tracked models with MLflow, you can use the
MLflow library to retrieve your experiments and its details.

1.  To list all experiments, use the following code. Use the **+
    Code** icon below the cell output to add a new code cell to the
    notebook, and enter the following code in it. Use the **▷ Run
    cell** button on the left of the cell to run it

+++import mlflow

experiments = mlflow.search_experiments()

for exp in experiments:

print(exp.name)+++

<img src="./media/image45.png" style="width:6.5in;height:3.64167in" />

2.  To retrieve a specific experiment, you can get it by its name. Use
    the **+ Code** icon below the cell output to add a new code cell to
    the notebook, and enter the following code in it. Use the **▷ Run
    cell** button on the left of the cell to run it

+++experiment_name = "experiment-diabetes"

exp = mlflow.get_experiment_by_name(experiment_name)

print(exp)+++

<img src="./media/image46.png"
style="width:7.01519in;height:3.07083in" />

3.  Using an experiment name, you can retrieve all jobs of that
    experiment. Use the **+ Code** icon below the cell output to add a
    new code cell to the notebook, and enter the following code in it.
    Use the **▷ Run cell** button on the left of the cell to run it.

+++ mlflow.search_runs(exp.experiment_id)+++

<img src="./media/image47.png"
style="width:7.04167in;height:2.47679in" />

4.  To more easily compare job runs and outputs, you can configure the
    search to order the results. For example, the following cell orders
    the results by *start_time*, and only shows a maximum of 2 results.

5.  Use the **+ Code** icon below the cell output to add a new code cell
    to the notebook, and enter the following code in it. Use the **▷ Run
    cell** button on the left of the cell to run it.

+++ mlflow.search_runs(exp.experiment_id, order_by=\["start_time
DESC"\], max_results=2)+++

<img src="./media/image48.png"
style="width:7.11389in;height:2.4625in" />

6.  Finally, you can plot the evaluation metrics of multiple models next
    to each other to easily compare models:

7.  Use the **+ Code** icon below the cell output to add a new code cell
    to the notebook, and enter the following code in it. Use the **▷ Run
    cell** button on the left of the cell to run it.

> +++import matplotlib.pyplot as plt
>
> df_results = mlflow.search_runs(exp.experiment_id,
> order_by=\["start_time DESC"\],
> max_results=2)\[\["metrics.training_r2_score", "params.estimator"\]\]
>
> fig, ax = plt.subplots()
>
> ax.bar(df_results\["params.estimator"\],
> df_results\["metrics.training_r2_score"\])
>
> ax.set_xlabel("Estimator")
>
> ax.set_ylabel("R2 score")
>
> ax.set_title("R2 score by Estimator")
>
> for i, v in enumerate(df_results\["metrics.training_r2_score"\]):
>
> ax.text(i, v, str(round(v, 2)), ha='center', va='bottom',
> fontweight='bold')
>
> plt.show()+++
>
> <img src="./media/image49.png"
> style="width:6.8546in;height:4.17083in" />

## Task 8: Explore your experiments

Microsoft Fabric will keep track of all your experiments and allows you
to visually explore them.

1.  Select **TrainModel_FabricXX** in the left navigation pane.

<img src="./media/image50.png"
style="width:5.85833in;height:6.96667in" />

2.  In the **TrainModel_FabricXX** pane ,Select
    the **experiment-diabetes** experiment to open it.

<img src="./media/image51.png" style="width:7.1635in;height:3.6875in" />

<img src="./media/image52.png"
style="width:7.3272in;height:4.32509in" />

3.  In the **experiment-diabetes** pane, Select the **View** tab and
    select **Run list**.

<img src="./media/image53.png" style="width:6.5in;height:4.53333in" />

<img src="./media/image54.png" style="width:6.5in;height:3.18472in"
alt="A screenshot of a computer Description automatically generated" />

4.  Select the two latest runs by checking each box.

<img src="./media/image55.png"
style="width:7.08891in;height:4.02917in" />

5.  As a result, your two last runs will be compared to each other in
    the **Metric comparison** pane. By default, the metrics are plotted
    by run name.

<img src="./media/image56.png" style="width:7.32989in;height:3.97349in"
alt="A screenshot of a computer Description automatically generated" />

6.  Select the **🖉** (Edit) button of the graph visualizing the mean
    absolute error for each run.and enter the below details

- Change the **visualization type** to **bar**.

- Change the **X-axis** to **estimator**.

- Select **Replace** and explore the new graph.

<img src="./media/image57.png" style="width:6.225in;height:6in" />

<img src="./media/image58.png" style="width:6.5in;height:4.07292in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image59.png"
style="width:6.65578in;height:4.5625in" />

<img src="./media/image60.png" style="width:7.07428in;height:3.47365in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image61.png"
style="width:7.05298in;height:3.6125in" />

<img src="./media/image62.png" style="width:7.36969in;height:3.59745in"
alt="A screenshot of a graph Description automatically generated" />

By plotting the performance metrics per logged estimator, you can review
which algorithm resulted in a better model.

## Task 9: Save the model

After comparing machine learning models that you’ve trained across
experiment runs, you can choose the best performing model. To use the
best performing model, save the model and use it to generate
predictions.

1.  In the experiment overview, ensure the **View** tab is selected and
    select **Run details**

<img src="./media/image63.png"
style="width:7.33029in;height:3.8625in" />

7.  Select the run with the highest Training R2 score and click on
    the** Save **in the Save run as model box (you may need to scroll to
    the right to see this).

<img src="./media/image64.png" style="width:7.2in;height:3.14769in" />

8.  Select **Save as ML model** in the newly opened pop-up window,
    select the **model** folder and name the model **model-diabetes**.
    Now click on the **Save**.

<img src="./media/image65.png"
style="width:3.20833in;height:3.46667in" />

9.  Select **View ML model** in the notification that appears at the top
    right of your screen when the model is created. You can also refresh
    the window. The saved model is linked under **Model versions**.

<img src="./media/image66.png"
style="width:3.14167in;height:2.33333in" />

<img src="./media/image67.png" style="width:7.03899in;height:4.16398in"
alt="A screenshot of a computer Description automatically generated" />

Note that the model, the experiment, and the experiment run are linked,
allowing you to review how the model is trained.

## Task 10: Save the notebook and end the Spark session

Now that you’ve finished training and evaluating the models, you can
save the notebook with a meaningful name and end the Spark session.

1.  Select **Notebook 1** in the left navigation pane.

<img src="./media/image68.png" style="width:6.5in;height:6.625in" />

2.  In the notebook menu bar, use the ⚙️ **Settings** icon to view the
    notebook settings

<img src="./media/image69.png"
style="width:6.49167in;height:4.19167in" />

3.  Set the **Name** of the notebook to **Train and compare models**,
    and then close the settings pane.

<img src="./media/image70.png" style="width:6.5in;height:3.95in" />

4.  On the notebook menu, select **Stop session** to end the Spark
    session.

## Task 11: Clean up resources

In this exercise, you have created a notebook and trained a machine
learning model. You used Scikit-Learn to train the model and MLflow to
track it´s performance.

If you’ve finished exploring your model and experiments, you can delete
the workspace you created for this exercise.

1.  In the bar on the left, select the icon for your workspace i.e
    **TrainModel_FabricXX** to view all of the items it contains.

> <img src="./media/image71.png" style="width:4.21016in;height:3.94975in"
> alt="A screenshot of a computer Description automatically generated" />

2.  In the menu on the toolbar, select **Workspace settings**.

> <img src="./media/image72.png" style="width:6.05417in;height:2.20417in"
> alt="A screenshot of a search Description automatically generated" />

5.  Select **General** and click on **Remove this workspace.**

> <img src="./media/image73.png" style="width:6.5in;height:5.36667in" />

6.  In the **Delete workspace?** dialog box, click on the **Delete**
    button.

> <img src="./media/image74.png" style="width:5.11389in;height:1.77292in"
> alt="A screenshot of a computer Description automatically generated" />

**Summary**

You’ve created a workspace in Microsoft Fabric with a trial enabled.
Then, you’ve proceeded to set up a data lakehouse, ingested data for
analysis, and created a notebook for interactive coding. You’ve loaded
data into both Pandas and Spark DataFrames, and subsequently trained
machine learning models using Scikit-Learn while tracking their
performance with MLflow. You’ve effectively managed experiments using
MLflow, listing, retrieving, and ordering runs. Additionally, you’ve
explored experiment results in Microsoft Fabric, visualizing and
comparing model accuracy. The best performing model was saved for future
use, and the notebook was appropriately named and saved. Finally, you’ve
completed the lab by cleaning up resources and deleting the workspace
created for the exercise.
