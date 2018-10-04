﻿---
title: Database Object (DAO)
TOCTitle: Database Object
ms:assetid: 6cf2ddf8-3957-a15e-5eeb-85f81c1e415e
ms:mtpsurl: https://msdn.microsoft.com/library/Ff195520(v=office.15)
ms:contentKeyID: 48545482
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm0
f1_categories:
- Office.Version=v15
---

# Database Object (DAO)


**Applies to**: Access 2013 | Office 2013

A **Database** object represents an open database.

## Remarks

You use the **Database** object and its methods and properties to manipulate an open database. In any type of database, you can:

  - Use the **Execute** method to run an action query.

  - Set the **Connect** property to establish a connection to an ODBC data source.

  - Set the **QueryTimeout** property to limit the length of time to wait for a query to execute against an ODBC data source.

  - Use the **RecordsAffected** property to determine how many records were changed by an action query.

  - Use the **OpenRecordset** method to execute a select query and create a **Recordset** object.

  - Use the **Version** property to determine which version of a database engine created the database.

With a Microsoft Access database engine database, you can also use other methods, properties, and collections to manipulate a **Database** object, as well as create, modify, or get information about its tables, queries, and relationships. For example, you can:

  - Use the **CreateTableDef** and **CreateRelation** methods to create tables and relations, respectively.

  - Use the **CreateProperty** method to define new **Database** properties.

  - Use the **CreateQueryDef** method to create a persistent or temporary query definition.

  - Use **MakeReplica**, **Synchronize**, and **PopulatePartial** methods to create and synchronize full or partial replicas of your database.

  - Set the **CollatingOrder** property to establish the alphabetic sorting order for character-based fields in different languages.

You use the **CreateDatabase** method to create a persistent **Database** object that is automatically appended to the **Databases** collection, thereby saving it to disk.

You don't need to specify the **DBEngine** object when you use the **OpenDatabase** method.

Opening a database with linked tables doesn't automatically establish links to the specified external files. You must either reference the table's **TableDef** or **Field** objects or open a **Recordset** object. If you can't establish links to these tables, a trappable error occurs. You may also need permission to access the database, or another user might have the database opened exclusively. In these cases, trappable errors occur.

When a procedure that declares a **Database** object has executed, local **Database** objects are closed along with any open **Recordset** objects. Any pending updates are lost and any pending transactions are rolled back, but no trappable error occurs. You should explicitly complete any pending transactions or edits and close **Recordset** objects and **Database** objects before exiting procedures that declare these object variables locally.

When you use one of the transaction methods (**BeginTrans**, **CommitTrans**, or **Rollback**) on the **Workspace** object, these transactions apply to all databases opened on the **Workspace** from which the **Database** object was opened. If you want to use independent transactions, you must first open an additional **Workspace** object, and then open another **Database** object in that **Workspace** object.


> [!NOTE]
> <P>You can open the same data source or database more than once, creating duplicate names in the <STRONG>Databases</STRONG> collection. You should assign <STRONG>Database</STRONG> objects to object variables and refer to them by variable name.</P>



## Example

This example creates a new **Database** object and opens an existing **Database** object in the default **Workspace** object. Then it enumerates the **Database** collection and the **Properties** collection of each **Database** object.

``` 
Sub DatabaseObjectX() 
 
 Dim wrkAcc As Workspace 
 Dim dbsNorthwind As Database 
 Dim dbsNew As Database 
 Dim dbsLoop As Database 
 Dim prpLoop As Property 
 
 Set wrkAcc = CreateWorkspace("AccessWorkspace", "admin", _ 
 "", dbUseJet) 
 
 ' Make sure there isn't already a file with the name of 
 ' the new database. 
 If Dir("NewDB.mdb") <> "" Then Kill "NewDB.mdb" 
 
 ' Create a new database with the specified 
 ' collating order. 
 Set dbsNew = wrkAcc.CreateDatabase("NewDB.mdb", _ 
 dbLangGeneral) 
 Set dbsNorthwind = wrkAcc.OpenDatabase("Northwind.mdb") 
 
 ' Enumerate the Databases collection. 
 For Each dbsLoop In wrkAcc.Databases 
 With dbsLoop 
 Debug.Print "Properties of " & .Name 
 ' Enumerate the Properties collection of each 
 ' Database object. 
 For Each prpLoop In .Properties 
 If prpLoop <> "" Then Debug.Print " " & _ 
 prpLoop.Name & " = " & prpLoop 
 Next prpLoop 
 End With 
 Next dbsLoop 
 
 dbsNew.Close 
 dbsNorthwind.Close 
 wrkAcc.Close 
 
End Sub 
 
```

This example uses **CreateDatabase** to create a new, encrypted **Database** object.

    Sub CreateDatabaseX() 
     
     Dim wrkDefault As Workspace 
     Dim dbsNew As DATABASE 
     Dim prpLoop As Property 
     
     ' Get default Workspace. 
     Set wrkDefault = DBEngine.Workspaces(0) 
     
     ' Make sure there isn't already a file with the name of 
     ' the new database. 
     If Dir("NewDB.mdb") <> "" Then Kill "NewDB.mdb" 
     
     ' Create a new encrypted database with the specified 
     ' collating order. 
     Set dbsNew = wrkDefault.CreateDatabase("NewDB.mdb", _ 
     dbLangGeneral, dbEncrypt) 
     
     With dbsNew 
     Debug.Print "Properties of " & .Name 
     ' Enumerate the Properties collection of the new 
     ' Database object. 
     For Each prpLoop In .Properties 
     If prpLoop <> "" Then Debug.Print " " & _ 
     prpLoop.Name & " = " & prpLoop 
     Next prpLoop 
     End With 
     
     dbsNew.Close 
     
    End Sub

