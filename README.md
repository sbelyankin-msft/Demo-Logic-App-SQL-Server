# Demo: Logic Apps + SQL Server

## Create Database and Schema
1. Go to https://ms.portal.azure.com/#create/Microsoft.SQLDatabase
2. Enter required information on `Basic` tab
3. Click `Next: Networking >`
4. Enabled `Allow Azure services and resources to access this server`
5. Click `Review + create`
6. Click `Create`
7. Wait for the resource to be created
8. Click `Go` to resource
9. Click `Query Editor`
10. Create schema
```
CREATE TABLE [dbo].[new_employees] (
    [id] INT IDENTITY (1, 1) NOT NULL,
    [first_name] VARCHAR (30) NOT NULL,
    [last_name] VARCHAR (30) NOT NULL
);

ALTER TABLE [dbo].[new_employees]
   ADD CONSTRAINT PK_employee_id PRIMARY KEY CLUSTERED (id);
```

## Create Logic App
1. In a new tab, go to https://ms.portal.azure.com/#create/Microsoft.LogicApp
2. Enter required information on `Basic` tab
3. Select the same Resource Group and Region as your database
4. Select Plan Type `Consumption`
5. Click `Review + create`
6. Click `Create`
7. Wait for the resource to be created
8. Click `Go` to resource
9. Click on the Logic App name in the navigation breadcrums
10. Click `Identity`
11. Enable `System assigned identity` and save


## Create Flow
1. Click `Logic app designer`
2. Click `Blank Logic App`
3. Select `SQL Server`
4. Select Trigger `When an item is created (V2)`
5. Enter value for Connection name
6. Select `Logic Apps Managed Identity` and click `Create`
7. Select/enter your database information
8. Click `+ New step`
9. Select `Office 365 Outlook`
10. Select `Send an email (V2)` and sign in
11. Click save





# Insert Records
1. Go back to the database tab
2. Execute insert statement
```
INSERT INTO [dbo].[new_employees] (first_name, last_name) VALUES('Bob', 'Smith');
```
