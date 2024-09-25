# Lab 04- Chatting with your data using AI Skills in Microsoft Fabric

With the Microsoft Fabric AI skill, you can make data more accessible to
your colleagues. You can configure a generative AI system to generate
queries that answer questions about your data. After you configure the
AI skill, you can share it with your colleagues, who can then ask their
questions in plain English. Based on their questions, the AI generates
queries over your data that answer those questions.

The AI skill relies on generative AI, specifically, large language
models (LLMs). These LLMs can generate queries, for example, T-SQL
queries, based on a specific schema and a question. The system sends a
question in the AI skill, information about the selected data (including
the table and column names, and the data types found in the tables) to
the LLM. Next, it requests generation of a T-SQL query that answers the
question. Parse the generated query to first ensure that it doesn't
change the data in any way. Then execute that query. Finally, show the
query execution results. An AI skill is intended to access specific
database resources, and then generate and execute relevant T-SQL
queries.

**Important Note**: When you take a break, please pause the Fabric
capacity in the Azure portal.

## **Task 0: Sync Host environment time**

1.  In your VM, navigate and click in the **Search bar**, type
    **Settings** and then click on **Settings** under **Best match**.

> <img src="./media/image1.png" style="width:4.65394in;height:3.99955in"
> alt="A screenshot of a computer Description automatically generated" />

2.  On Settings window, navigate and click on **Time & language**.

<img src="./media/image2.png" style="width:5.92237in;height:5.21371in"
alt="A screenshot of a computer Description automatically generated" />

3.  On **Time & language** page, navigate and click on **Date & time**.

<img src="./media/image3.png" style="width:6.5in;height:5.27639in"
alt="A screenshot of a computer Description automatically generated" />

4.  Scroll down and navigate to **Additional settings** section, then
    click on **Syn now** button. It will take 3-5 minutes to syn.

<img src="./media/image4.png" style="width:6.5in;height:5.04861in"
alt="A screenshot of a computer Description automatically generated" />

5.  Close the **Settings** window.

<img src="./media/image5.png" style="width:6.48341in;height:5.10915in"
alt="A screenshot of a computer Description automatically generated" />

## Task 0: Redeem Azure Pass

1.  Open a new tab on your browser and enter the following link in the
    address bar: <https://www.microsoftazurepass.com/>

2.  Then, click on the **Start button.**

<img src="./media/image6.png" style="width:6.26806in;height:2.56389in"
alt="A person using a computer Description automatically generated" />

**Note**: Do not use your Company/Work Account to login to redeem the
Azure Pass, another Azure Pass will not be issued.

3.  Click on the **Resources** tab of the Lab VM and enter the **Office
    365 tenant credentials** to **Sign In**.

> <img src="./media/image7.png" style="width:3.59198in;height:3.64198in"
> alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image8.png" style="width:2.2729in;height:1.76038in"
alt="Graphical user interface, application Description automatically generated" />

4.  Crosscheck the Email ID and then click on the **Confirm Microsoft
    Account**.

<img src="./media/image9.png" style="width:6.26806in;height:2.16389in"
alt="Text Description automatically generated" />

5.  Click on the **Resources** tab and copy the **Promo Code**. Navigate
    to **Enter Promo code** box and paste the Promo Code that have you
    copied, then click on the **Claim Promo Code button.**

> <img src="./media/image10.png" style="width:3.50864in;height:3.25028in"
> alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image11.png" style="width:6.26806in;height:2.63056in"
alt="Graphical user interface, text, application Description automatically generated" />

6.  Enter correct details in **Your Profile** page, tick all the check
    boxes, and then click on **Sign up** button.

<img src="./media/image12.jpeg" style="width:4.1209in;height:2.696in"
alt="A screenshot of a computer Description automatically generated with medium confidence" />

<img src="./media/image13.png" style="width:3.1677in;height:2.57283in"
alt="Graphical user interface, text, application Description automatically generated" />

7.  On **Are you satisfied with your signup experience** window, enter
    your feedback and click on the **Submit** button.

<img src="./media/image14.png"
style="width:3.72271in;height:3.63271in" />

8.  It would automatically redirect you to the Azure Portal and now you
    are ready to use Azure services. On **Welcome to Microsoft Azure**
    dialog box, click on the **Maybe later** button.

<img src="./media/image15.png" style="width:6.26806in;height:4.21736in"
alt="A screenshot of a computer Description automatically generated" />

## Task 1: Sign in to Power BI account and sign up for the free [Microsoft Fabric trial](https://learn.microsoft.com/en-us/fabric/get-started/fabric-trial)

1.  Open your browser, navigate to the address bar, and type or paste
    the following URL: !!https://app.fabric.microsoft.com/!! then press
    the **Enter** button.

> <img src="./media/image16.png" style="width:6.5in;height:2.89653in"
> alt="A search engine window with a red box Description automatically generated with medium confidence" />

2.  In the **Microsoft Fabric** window, enter your given credentials,
    and click on the **Submit** button.

> <img src="./media/image17.png" style="width:6.49167in;height:3.11667in"
> alt="A close up of a white and green object Description automatically generated" />

3.  Then, In the **Microsoft** window enter the password and click on
    the **Sign in** button**.**

> <img src="./media/image18.png" style="width:4.50833in;height:3.83333in"
> alt="A login screen with a red box and blue text Description automatically generated" />

4.  In **Stay signed in?** window, click on the **Yes** button.

> <img src="./media/image19.png" style="width:4.58333in;height:3.66667in"
> alt="A screenshot of a computer error Description automatically generated" />

5.  You’ll be directed to Power BI Home page.

<img src="./media/image20.png" style="width:7.17276in;height:3.31357in"
alt="A screenshot of a computer Description automatically generated" />

6.  On **Power BI Home** page, click on the **Account manager** on the
    right side. In the Account manager blade, navigate and
    select **Start trial as shown in the below image.**

<img src="./media/image21.png" style="width:7.22864in;height:1.92083in"
alt="A screenshot of a computer Description automatically generated" />

7.  If prompted, agree to the terms and then select **Start trial**.

> <img src="./media/image22.png" style="width:6.5in;height:1.64167in"
> alt="A screenshot of a computer Description automatically generated" />

8.  Once your trial capacity is ready, you receive a confirmation
    message. Select **Fabric Home Page** to begin working in Fabric.

> <img src="./media/image23.png" style="width:5.54167in;height:2.01667in"
> alt="A screenshot of a computer Description automatically generated" />

9.  Open your Account manager again. Notice that you now have a heading
    for **Trial status**. Your Account manager keeps track of the number
    of days remaining in your trial. You will also see the countdown in
    your Fabric menu bar when you work in a product experience.

> <img src="./media/image24.png" style="width:6.5in;height:3.80833in"
> alt="A screenshot of a computer Description automatically generated" />

## Task 2: Create Fabric Capacity using Azure portal 

Microsoft Fabric is deployed to an Azure Active Directory tenant. Within
each Fabric tenant, Fabric capacities can be created to group resources
for various purposes -- this might be done organizationally (sales,
marketing, development), geographically, or other logical grouping.

If a Fabric Trial is available, we recommend taking advantage of that
opportunity to try Microsoft Fabric for a period of time (currently 60
days) with no commitment. To see if you are in a trial or eligible for a
trial, visit the [Fabric portal](https://app.fabric.microsoft.com/). If
you are able to log in or presented the option to start a trial, you
should be all set!

To create a Fabric capacity outside of a trial environment, create a new
resource from the Azure portal, and search for Fabric.

1.  Open your browser, navigate to the address bar, type or paste the
    following URL: !!https://portal.azure.com/!!, then press the
    **Enter** button.

2.  From the Azure portal home page, click on **Azure portal menu**
    represented by three horizontal bars on the left side of the
    Microsoft Azure command bar as shown in the below image.

> <img src="./media/image25.png" style="width:6.5in;height:3.19167in"
> alt="A screenshot of a computer Description automatically generated" />

3.  Navigate and click on **+ Create a resource**.

> <img src="./media/image26.png" style="width:4.35417in;height:4.6875in"
> alt="A screenshot of a computer Description automatically generated" />

4.  On **Create a resource** page, in the **Search services and
    marketplace** search bar, type!!**Fabric!!**, then select
    **Microsoft fabric**.

> <img src="./media/image27.png" style="width:6.5in;height:5.19167in"
> alt="A screenshot of a computer Description automatically generated" />

5.  In the **Marketplace** page, navigate to the **Microsoft Fabric**
    section, click on the **Create** button dropdown, then select
    **Microsoft Fabric** as shown in the image.

> <img src="./media/image28.png" style="width:6.49167in;height:5.49167in"
> alt="A screenshot of a computer Description automatically generated" />

6.  In the **Create Fabric capacity** window, under the **Basics** tab,
    enter the following details and click on the **Review+create**
    button.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 74%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Subscription</strong></th>
<th><blockquote>
<p>Select the assigned subscription</p>
</blockquote></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Resource group</strong></td>
<td>Click on <strong>Create new</strong>&gt; enter
!!<strong>AI-Skill-FabricXXX!!</strong>(XXX can be a unique number, you
can add more digits after XXX to make the name unique)</td>
</tr>
<tr class="even">
<td><strong>Capacity name</strong></td>
<td><strong>!!aiskillfabric789!!</strong>( XXX can be a unique number,
you can add more digits after XXX to make the name unique)</td>
</tr>
<tr class="odd">
<td><strong>Region</strong></td>
<td>Select near by available region, in this lab <strong>West US
3</strong> is using for this resource</td>
</tr>
<tr class="even">
<td><strong>Size</strong></td>
<td>select <strong>F64</strong> SKU</td>
</tr>
</tbody>
</table>

> <img src="./media/image29.png" style="width:6.5in;height:6.30833in" />
>
> <img src="./media/image30.png" style="width:6.49167in;height:6.425in" />

7.  Once the Validation is succeeded, click on the **Create** button.

> <img src="./media/image31.png" style="width:6.49167in;height:5.88333in"
> alt="A screenshot of a computer Description automatically generated" />
>
> <img src="./media/image32.png" style="width:6.5in;height:3.38819in"
> alt="A screenshot of a computer Description automatically generated" />

8.  After the deployment is completed, click on the **Go to resource**
    button.

> <img src="./media/image33.png" style="width:6.5in;height:3.24722in"
> alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image34.png" style="width:7.03724in;height:3.12466in"
alt="A screenshot of a computer Description automatically generated" />

## **Task 3: Create a Fabric workspace**

In this task, you create a Fabric workspace. The workspace contains all
the items needed for this lakehouse tutorial, which includes lakehouse,
dataflows, Data Factory pipelines, the notebooks, Power BI datasets, and
reports.

1.  Open your browser, navigate to the address bar, and type or paste
    the following URL: !!https://app.fabric.microsoft.com/!! then press
    the **Enter** button.

> <img src="./media/image16.png" style="width:6.5in;height:2.89653in"
> alt="A search engine window with a red box Description automatically generated with medium confidence" />

2.  In the **Microsoft Fabric** window, enter your credentials, and
    click on the **Submit** button.

> <img src="./media/image17.png" style="width:6.49167in;height:3.11667in"
> alt="A close up of a white and green object Description automatically generated" />

3.  Then, In the **Microsoft** window enter the password and click on
    the **Sign in** button**.**

> <img src="./media/image18.png" style="width:4.50833in;height:3.83333in"
> alt="A login screen with a red box and blue text Description automatically generated" />

4.  In **Stay signed in?** window, click on the **Yes** button.

> <img src="./media/image19.png" style="width:4.58333in;height:3.66667in"
> alt="A screenshot of a computer error Description automatically generated" />

5.  You’ll be directed to Power BI Home page.

<img src="./media/image35.png" style="width:6.49167in;height:4.1in"
alt="A screenshot of a computer Description automatically generated" />

6.  Go back to **Power BI** window. On the left side navigation menu of
    Power BI Home page, navigate and click on **Workspaces**.

<img src="./media/image36.png"
style="width:5.10625in;height:6.34583in" />

7.  In the Workspaces pane, click on **+** **New workspace button.**

> <img src="./media/image37.png" style="width:3.69844in;height:6.4125in"
> alt="A screenshot of a computer Description automatically generated" />

8.  In the **Create a workspace** pane that appears on the right side,
    enter the following details, and click on the **Apply** button.

| **Name** | ***!!A**I**-Fabric-XXX!!** (*XXX can be a unique number) (here, we entered ***A**I**-Fabric-XX -789***) |
|----|----|
| **Advanced** | Under **License mode**, select **Fabric** |
| **Default storage format** | **Small dataset storage format** |
| **C**apacity | **aiskillfabricXXX-** |
| **Template apps** | **Check the Develop template apps** |

> <img src="./media/image38.png" style="width:4.75in;height:4.9875in"
> alt="A screenshot of a computer Description automatically generated" />
>
> <img src="./media/image39.png"
> style="width:5.45833in;height:6.95833in" />

9.  Wait for the deployment to complete. It takes 2-3 minutes to
    complete.

<img src="./media/image40.png" style="width:6.5in;height:5.18611in"
alt="A screenshot of a computer Description automatically generated" />

## Task 4: Copilot tenant settings

1.  On right side of Power BI home page, click on the **Settings** icon.

2.  In **Settings** pane, scroll down to **Governance and insights**,
    then click on **Admin portal** .

<img src="./media/image41.png"
style="width:3.30833in;height:7.38333in" />

3.  In **Admin portal** pane, select **Tenant settings**, scroll down to
    **Copilot and Azure OpenAI Service** section, click on **Users can
    use Copilot and other features powered by Azure OpenAI**, then
    enable it using the **toggle** button. After **Users can use Copilot
    and other features powered by Azure OpenAI** were Enabled, click on
    the **Apply** button.

<img src="./media/image42.png"
style="width:6.8875in;height:6.54268in" />

<img src="./media/image43.png" style="width:3.58364in;height:0.80007in"
alt="A white background with black text Description automatically generated" />

4.  In **Admin portal** pane, select **Tenant settings**, scroll down to
    **Copilot and Azure OpenAI Service** section, click on **Data sent
    to Azure OpenAI can be processed outside your capacity's geographic
    region, compliance boundary, or national cloud instance**, then
    enable it using the **toggle** button. After **Data sent to Azure
    OpenAI can be processed outside your capacity's geographic region,
    compliance boundary, or national cloud instance** were Enabled,
    click on the **Apply** button.

<img src="./media/image44.png"
style="width:7.12426in;height:4.6125in" />

<img src="./media/image43.png" style="width:3.58364in;height:0.80007in"
alt="A white background with black text Description automatically generated" />

## **Task 5: Create a lakehouse**

1.  In the **AI-Fabric-XXX** page, click on the **Power BI** icon
    located at the bottom left and select **Data Engineering** under
    Synapse.

> <img src="./media/image45.png" style="width:6.5in;height:6.875in" />

2.  In the **Synapse** **Data Engineering** **Home** page,
    select **Lakehouse** to create a lakehouse.

<img src="./media/image46.png" style="width:6.5in;height:4.13333in" />

3.  In the **New lakehouse** dialog box, enter
    !!**AI_Fabric_lakehouseXX**!! in the **Name** field, click on the
    **Create** button and open the new lakehouse.

> **Note**: Ensure to remove space before **AI_Fabric_lakehouseXX**.
>
> <img src="./media/image47.png" style="width:2.975in;height:1.80833in" />

4.  You will see a notification stating **Successfully created SQL
    endpoint**.

> <img src="./media/image48.png" style="width:3.10027in;height:2.60023in"
> alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image49.png" style="width:6.5in;height:4.81875in"
alt="A screenshot of a computer Description automatically generated" />

5.  Next, create a new notebook to query the table. In
    the **Home** ribbon, select the drop down for **Open notebook** and
    choose **New notebook**.

<img src="./media/image50.png" style="width:6.5in;height:4.44167in" />

## Task 6: Upload AdventureWorksDW data into lakehouse

First, create a lakehouse and populate it with the necessary data.

If you already have an instance of AdventureWorksDW in a warehouse or
lakehouse, you can skip this step. If not, create a lakehouse from a
notebook. Use the notebook to populate the lakehouse with the data.

1.  In the query editor, copy and paste the following code. Select
    the **Run all** button to execute the query. After the query is
    completed, you will see the results.

<span class="mark">!!import pandas as pd</span>

<span class="mark">from tqdm.auto import tqdm</span>

<span class="mark">base =
"https://synapseaisolutionsa.blob.core.windows.net/public/AdventureWorks"</span>

<span class="mark">\# load list of tables</span>

<span class="mark">df_tables = pd.read_csv(f"{base}/adventureworks.csv",
names=\["table"\])</span>

<span class="mark">for table in (pbar :=
tqdm(df_tables\['table'\].values)):</span>

<span class="mark">pbar.set_description(f"Uploading {table} to
lakehouse")</span>

<span class="mark">\# download</span>

<span class="mark">df =
pd.read_parquet(f"{base}/{table}.parquet")</span>

<span class="mark">\# save as lakehouse table</span>

<span class="mark">spark.createDataFrame(df).write.mode('overwrite').saveAsTable(table)</span>!!

<img src="./media/image51.png"
style="width:7.35887in;height:3.7125in" />

<img src="./media/image52.png" style="width:7.1014in;height:3.80107in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image53.png" style="width:7.11062in;height:4.00352in"
alt="A screenshot of a computer Description automatically generated" />

After a few minutes, the lakehouse is populated with the necessary data.

## Task 7: Create an AI skill

1.  To create a new AI skill, go to the **Data Science** experience and
    select **AI Skill**.

<img src="./media/image54.png"
style="width:6.43333in;height:7.69167in" />

1.  In the Data Science home page, select **AI Skill(Preview).**

<img src="./media/image55.png" style="width:6.5in;height:3.74167in" />

2.  In the **Create AI skill** dialog box, enter !!**AISkillsFabric**!!
    in the **Name** field, click on the **Create** button.

<img src="./media/image56.png"
style="width:2.64167in;height:2.30833in" />

3.  In **Select a lakehouse SQL endpoint for the model to reference.
    You’ll select specific tables in the next step** page, select your
    lakehouse i.e., **AI_Fbric_lakehouseXX**, then click on the
    **Confirm** button.

<img src="./media/image57.png"
style="width:7.2125in;height:4.37009in" />

<img src="./media/image58.png" style="width:7.23601in;height:4.31919in"
alt="A screenshot of a computer Description automatically generated" />

4.  You must then select the tables for which you want the AI skill to
    have available access.

This lab uses these tables:

- DimCustomer

- DimDate

- DimGeography

- DimProduct

- DimProductCategory

- DimPromotion

- DimReseller

- DimSalesTerritory

- FactInternetSales

- FactResellerSales

<span class="mark">**Important Note:** If you face any SKU issues,
please check the workspace License
info.</span><img src="./media/image59.png"
style="width:7.30313in;height:3.2625in" />

## Task 8: Provide instructions

1.  When you first ask the AI skill questions with the listed tables
    select **factinternetsales**, the AI skill answers them fairly well.

2.  For instance, for the question !!**What is the most sold
    product?!!**, the AI skill returns:

<img src="./media/image60.png"
style="width:6.49167in;height:3.94167in" />

<img src="./media/image61.png"
style="width:6.49167in;height:4.03333in" />

3.  Copy the all question and SQL queries and paste them in a notepad
    and then Save the notepad to use the information in the upcoming
    tasks

4.  Select FactResellerSales and enter the following text and click on
    the **Submit icon** as shown in the below image.

!!**What is our most sold product?**!!

<img src="./media/image62.png"
style="width:6.87917in;height:3.94735in" />

As you continue to experiment with queries, you should add more
instructions.

5.  Select the **dimcustomer** , enter the following text and click on
    the **Submit icon**

!!**how many active customers did we have June 1st, 2013?**!!

<img src="./media/image63.png"
style="width:6.49167in;height:3.83333in" />

<img src="./media/image64.png" style="width:6.5in;height:3.75069in" />

6.  Select the **dimdate,** **FactInternetSales** , enter the following
    text and click on the **Submit icon**

!!**what are the monthly sales trends for the last year?**!!

<img src="./media/image65.png" style="width:7.37104in;height:4.29583in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image66.png" style="width:7.22903in;height:4.14279in"
alt="A screenshot of a computer Description automatically generated" />

7.  Select the **dimproduct,** **FactInternetSales** , enter the
    following text and click on the **Submit icon**

!!**which product category had the highest average sales price?**!!

<img src="./media/image67.png"
style="width:7.3875in;height:4.52354in" />

<img src="./media/image68.png"
style="width:7.02396in;height:4.18511in" />

Part of the problem is that "active customer" doesn't have a formal
definition. More instructions in the notes to the model text box might
help, but users might frequently ask this question. You need to make
sure that the AI handles the question correctly

8.  The relevant query is moderately complex, so provide an example by
    selecting the edit button.

<img src="./media/image69.png" style="width:3in;height:4.43333in" />

9.  In the Example SQL queries tab, select the **+Add example.**

<img src="./media/image70.png"
style="width:6.49167in;height:3.30833in" />

10. You can manually add examples, but you can also upload them from a
    JSON file. Providing examples from a file is helpful when you have
    many SQL queries that you want to upload all at once, instead of
    manually uploading the queries one by one.

11.  Add all the queries and SQL queries that you have saved in Notepad,
    and then click on ‘Download all as .json’.

<img src="./media/image71.png"
style="width:7.3149in;height:3.17917in" />

## Task 9: Use the AI skill programmatically

Both instructions and examples were added to the AI skill. As testing
proceeds, more examples and instructions can improve the AI skill even
further. Work with your colleagues to see if you provided examples and
instructions that cover the kinds of questions they want to ask.

You can use the AI skill programmatically within a Fabric notebook. To
determine whether or not the AI skill has a published URL value.

1.  In the AISkillFabric page, in the **Home** ribbon select the
    **Settings**.

<img src="./media/image72.png"
style="width:7.30417in;height:3.68018in" />

2.  Before you publish the AI skill, it doesn't have a published URL
    value, as shown in this screenshot.

3.  Close the AI Skill setting.

<img src="./media/image73.png"
style="width:7.40872in;height:2.8875in" />

4.  In the **Home** ribbon, select the **Publish**.

<img src="./media/image74.png"
style="width:7.24097in;height:4.1125in" />

<img src="./media/image75.png" style="width:2.60833in;height:1.5in" />

<img src="./media/image76.png" style="width:3.05026in;height:1.05009in"
alt="A white rectangular sign with green and black text Description automatically generated" />

5.  After publishing, select ‘Settings’ from the Home ribbon

<img src="./media/image77.png" style="width:6.5in;height:4.11667in" />

6.  The published URL for the AI skill appears, as shown in this
    screenshot.

7.  Copy the URL and paste that in a notepad and then Save the notepad
    to use the information in the upcoming

<img src="./media/image78.png"
style="width:7.10409in;height:1.93333in" />

8.  Select **Notebook1** in the left navigation pane.

<img src="./media/image79.png" style="width:6.5in;height:5.84167in" />

9.  Use the **+ Code** icon below the cell output to add a new code cell
    to the notebook, enter the following code in it and replace the
    **URL**. Click on **▷ Run** button and review the output

<span class="mark">!!import requests</span>

<span class="mark">import json</span>

<span class="mark">import pprint</span>

<span class="mark">from synapse.ml.mlflow import
get_mlflow_env_config</span>

<span class="mark">\# the URL could change if the workspace is assigned
to a different capacity</span>

<span class="mark">url = "https://\<generic published URL
value\>"</span>

<span class="mark">configs = get_mlflow_env_config()</span>

<span class="mark">headers = {</span>

<span class="mark">"Authorization": f"Bearer
{configs.driver_aad_token}",</span>

<span class="mark">"Content-Type": "application/json;
charset=utf-8"</span>

<span class="mark">}</span>

<span class="mark">question = "{userQuestion: \\what is an example
product?\\}"</span>

<span class="mark">response = requests.post(url, headers=headers, data =
question)</span>

<span class="mark">print("RESPONSE: ", response)</span>

<span class="mark">print("")</span>

<span class="mark">response = json.loads(response.content)</span>

<span class="mark">print(response\["result"\])</span>!!

<img src="./media/image80.png" style="width:6.49167in;height:3.425in" />

<img src="./media/image81.png" style="width:6.5in;height:4.30833in" />

## Task 10: Delete the resources

To avoid incurring unnecessary Azure costs, you should delete the
resources you created in this quickstart if they're no longer needed. To
manage resources, you can use the [Azure
portal](https://portal.azure.com/?azure-portal=true).

1.  To delete the storage account, navigate to **Azure portal Home**
    page, click on **Resource groups**.

> <img src="./media/image82.png" style="width:6.5in;height:4.58472in"
> alt="A screenshot of a computer Description automatically generated" />

2.  Click on the assigned resource group.

<img src="./media/image83.png" style="width:6.275in;height:3.9in" />

3.  In the **Resource group** home page, select the **delete resource
    group**

> <img src="./media/image84.png" style="width:6.5in;height:3.975in" />

4.  In the **Delete Resources** pane that appears on the right side,
    navigate to **Enter “resource group name” to confirm deletion**
    field, then click on the **Delete** button.

5.  On **Delete confirmation** dialog box, click on **Delete** button.

> <img src="./media/image85.png" style="width:3.475in;height:1.85833in"
> alt="A screenshot of a computer error Description automatically generated" />

6.  Click on the bell icon, you’ll see the notification –**Deleted
    resource group AI-Skill-Fabric890**

<img src="./media/image86.png" style="width:4.39205in;height:1.70848in"
alt="A screenshot of a web page Description automatically generated" />

7.  Open your browser, navigate to the address bar, and type or paste
    the following URL: !!https://app.fabric.microsoft.com/!! then press
    the **Enter** button.

> <img src="./media/image87.png" style="width:3.75in;height:4.025in" />

8.  Select the ***...*** option under the workspace name and
    select **Workspace settings**.

<img src="./media/image88.png"
style="width:7.36471in;height:2.05417in" />

9.  Select **General** and click on **Remove this workspace.**

<img src="./media/image89.png" style="width:6.5in;height:5.03056in"
alt="A screenshot of a computer settings Description automatically generated" />

10. Click on **Delete** in the warning that pops up.

<img src="./media/image90.png" style="width:5.85051in;height:1.62514in"
alt="A white background with black text Description automatically generated" />

11. Wait for a notification that the Workspace has been deleted, before
    proceeding to the next lab.

<img src="./media/image91.png" style="width:6.5in;height:2.15208in"
alt="A screenshot of a computer Description automatically generated" />
