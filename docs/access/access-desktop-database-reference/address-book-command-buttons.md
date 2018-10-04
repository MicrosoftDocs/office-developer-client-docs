---
title: Address Book Command Buttons
TOCTitle: Address Book Command Buttons
ms:assetid: bcea6f53-3e36-b067-03c2-b157ed02d41d
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249908(v=office.15)
ms:contentKeyID: 48547422
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Address Book Command Buttons


**Applies to**: Access 2013 | Office 2013


The Address Book application includes the following command buttons:

  - A Find button to submit a query to the database.

  - A **Clear** button to clear the text boxes before starting a new search.

  - An Update Profile button to save changes to an employee record.

  - A Cancel Changes button to discard changes.

## Find Button

Clicking the **Find** button activates the VBScript Find\_OnClick Sub procedure, which builds and sends the SQL query. Clicking this button populates the data grid.

## Building the SQL Query

The first part of the Find\_OnClick Sub procedure builds the SQL query, one phrase at a time, by appending text strings to a global SQL SELECT statement. It begins by setting the variable to a SQL SELECT statement that requests all rows of data from the data source table. Next, the Sub procedure scans each of the four input boxes on the page.

Because the program uses the word in building the SQL statements, the queries are substring searches rather than exact matches.

For example, if the **Last Name** box contained the entry "Berge" and the **Title** box contained the entry "Program Manager", the SQL statement (value of ) would read:

``` 
 
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%' 
```

If the query was successful, all persons with a last name containing the text "Berge" (such as Berge and Berger) and with a title containing the words "Program Manager" (for example, Program Manager, Advanced Technologies) are displayed in the HTML data grid.

## Preparing and Sending the Query

The last part of the Find\_OnClick Sub procedure consists of two statements. The first statement assigns the SQL property of the RDS.DataControl object equal to the dynamically built SQL query. The second statement causes the **RDS.DataControl** object () to query the database, and then display the new results of the query in the grid.

``` 
 
Sub Find_OnClick 
 '... 
 DC1.SQL = myQuery 
 DC1.Refresh 
End Sub 
```

## Update Profile Button

Clicking the **Update Profile** button activates the VBScript Update\_OnClick Sub procedure, which executes the RDS.DataControl object's () SubmitChanges and Refresh methods.

``` 
 
Sub Update_OnClick 
 DC1.SubmitChanges 
 DC1.Refresh 
End Sub 
```

When DC1.SubmitChanges executes, the Remote Data Service packages all the update information and sends it to the server via HTTP. The update is all-or-nothing; if a part of the update is unsuccessful, none of the changes is made, and a status message is returned. executes, the Remote Data Service packages all the update information and sends it to the server via HTTP. The update is all-or-nothing; if a part of the update is unsuccessful, none of the changes is made, and a status message is returned. DC1.Refresh isn't necessary after **SubmitChanges** with Remote Data Service, but it ensures fresh data.

## Cancel Changes Button

Clicking **Cancel Changes** activates the VBScript Cancel\_OnClick Sub procedure, which executes the RDS.DataControl object's ( CancelUpdate method.

``` 
 
Sub Cancel_OnClick 
 DC1.CancelUpdate 
End Sub 
```

When executes, it discards any edits that a user has made to an employee record on the data grid since the last query or update. It restores the original values.

