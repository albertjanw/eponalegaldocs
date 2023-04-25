# Installing the Epona DMSforLegal365 APPs

## Goal

- Deploy Azure SQL database and Azure storage account at the client

- Connect Epona DMSforLegal365 APP services to these accounts

- Deploy the APP services

## Required information

IP addresses of Epona APP services (per 1 July 2021, subject to change):

13.75.146.18

52.233.190.74

20.43.22.54

52.165.153.69

## Azure configuration steps

1. Check the Azure subscription that you are going to use. Azure
    services are placed in resource groups and can be connected to a
    subscription.

![](./assets/image1.png)

2. Create the Azure SQL resource

![](./assets/image2.png)
\
3. Choose Azure SQL and select Create

![](./assets/image3.png)
\
4. Choose a **Single database**

![](./assets/image4.png)

5\. Select the appropriate subscription (financial consequences) and the
resource group

![](./assets/image5.png)

6\. Define the Database name and the database server, in this case a new
database server is created.

![](./assets/image6.png)

7\. The database server can host multiple databases, in this case for
the DMSforLegal365 Database a separate database server is created

![](./assets/image7.png)

Choose the Location according to you compliance needs

8\. The database and database server are selected

![](./assets/image8.png)

9\. Geo redundancy is not required, there is data in this database that
can be recreated

![](./assets/image9.png)

10\. Choose Additional settings and change the collation of the database

![](./assets/image10.png)

11\. Ensure you choose: **SQL_Latin1_General_CP850_BIN2**

![](./assets/image11.png)

12\. No SQL Defender services are required

![](./assets/image12.png)

13\. The Tab Networking is important. This is a public available SQL
database that can be accessed by a specific set of IP adresses of
servers from Epona. Choose Public endpoint, at this moment the set of
Epona IP adresses cannot be defined

![](./assets/image13.png)

14\. On the tab TAGs you can define billings tags of this service

![](./assets/image14.png)

15\. Wait untill the deployment completes

![](./assets/image15.png)

16\. Create a SQL user

Connect with SQl Studio to the Azure SQL database

![](./assets/image16.png)

17\. Get the Connection String

![](./assets/image17.png)

![](./assets/image18.png)

**Remark**: the Epona server IP addresses need access to this resource
and a connection string is required with the right username and password

## Setting up the Azure Storage account

1. Choose Create a resource, Storage Account

    ![](./assets/image19.png)

2. Define the subscription, resource group and assign a name to the
    account

    ![](./assets/image20.png)

    Choose your Region of preference

3. Define TAGS for billing purposes

    ![](./assets/image21.png)

4. Review & Create the storage account

    ![](./assets/image22.png)

5. Copy the Connection String

    ![](./assets/image23.png)

    ![](./assets/image24.png)

    Save the connection string in a safe/ vault for later use

# DMSforLegal 365 Portal actions

- Visit the <https://dmsforlegal365.epona.com/#/setup> portal as
    Global Admin to deploy the EmailFiling and DMSforLegal365 APPs to
    your tenant

![](./assets/image25.png)

- Choose **Give consent** to consent to the deployment of these APPs

![](./assets/image26.png)

![](./assets/image27.png)

- Deploy the two APPs, copy the URL to the Custom XML in clipboard

![](./assets/image28.png)

- Enter the URL including HTTPS:// (yes, confusing dialog)

![](./assets/image29.png)

- Define the users or group to deploy it to

![](./assets/image30.png)

- Confirm the deployment

![](./assets/image31.png)

- Now add the other, i.c. Office APP

![](./assets/image32.png)

- The two apps have been deployed

![](./assets/image33.png)

## DMSforLegal365 Setting and configuring Machine Learning

- Initially the DMSforLegal365 settings will point to the root site

    ![](./assets/image34.png)

- Change the Sharepoint URL to reflect the location that hosts the
    Matters, Clients and other DMSforLegal lists

    ![](./assets/image35.png)

- Switch on keyword correlation, there is a Managed choice (hosted in
    Azure by Epona) and a Custom choice. Custom is selected, which means
    that the APP requires connection information to the Azure SQL
    database in your own Azure tenant

    ![](./assets/image36.png)

- Enter the SQL connection string with the appropriate server name,
    login, password information

    ![](./assets/image37.png)

- Choose Initialize database

    ![](./assets/image38.png)

- Click Log to see if the connection information was correct and the
    database intialization has started with the populartion of standard
    data

    ![](./assets/image39.png)

- A Give consent stage is required to allow the APP services to crawl
    existing items and add them to the prediction database

    ![](./assets/image40.png)

    ![](./assets/image41.png)

- Next stage is to activate the OCR crawler process

    ![](./assets/image42.png)

- The OCR service also requires consent. These permissions are
    different from the above consent, because the OCR process is also
    able to write data

    ![](./assets/image43.png)

    ![](./assets/image44.png)

- Enable Delta allows the OCR process to find new Matters and new
    document items

    ![](./assets/image45.png)

- The last stage is to activate Machine Learning. This is more
    extensive than Predictive EmailFiling. Machine Learnings builds a
    database of keywords and requires Azure SQL database and Azure
    storage access

    ![](./assets/image46.png)

- In this case Custom storage is selected. The data is stored in your
    own tenant
    Enter the connection string to the Azure storage resource

    ![](./assets/image47.png)

- Enable Delta machine learning cycles

    ![](./assets/image48.png)

    This is the delta crawling process. It does not trigger complete
    recalculation of the training data, this is a manual step.
