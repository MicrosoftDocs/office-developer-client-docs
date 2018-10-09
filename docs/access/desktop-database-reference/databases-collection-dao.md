---
title: Databases Collection (DAO)
TOCTitle: Databases Collection
ms:assetid: 988ae6f5-ec15-cd1c-191d-f295624425f4
ms:mtpsurl: https://msdn.microsoft.com/library/Ff197944(v=office.15)
ms:contentKeyID: 48546493
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Databases Collection (DAO)

**Applies to**: Access 2013 | Office 2013

A **Databases** collection contains all open **Database** objects opened or created in a **Workspace** object.

## Remarks

When you open an existing **Database** object or create a new one from a **Workspace**, it is automatically appended to the **Databases** collection. When you close a **Database** object with the **[Close](connection-close-method-dao.md)** method, it is removed from the **Databases** collection but not deleted from disk. You should close all open **Recordset** objects before closing a **Database** object.

In a Microsoft Access workspace, the **Name** property setting of a database is a string that specifies the path of the database file.

To refer to a **Database** object in a collection by its ordinal number or by its **Name** property setting, use any of the following syntax forms:

- **Databases**(0)

- **Databases**("*name*")

- **Databases**\!\[*name*\]

> [!NOTE]
> You can open the same data source or database more than once, creating duplicate names in the **Databases** collection. You should assign **Database** objects to object variables and refer to them by variable name.

## Example

This example creates a new **Database** object and opens an existing **Database** object in the default **Workspace** object. Then it enumerates the **Database** collection and the **Properties** collection of each **Database** object.

```vb 
Sub DatabaseObjectX() 
 
 Dim wrkAcc As Workspace 
 Dim dbsNorthwind As Database 
 Dim dbsNew As Database 
 Dim dbsLoop As Database 
 Dim prpLoop As Property 
 
 Set wrkAcc = CreateWorkspace("AccWorkspace", "admin", _ 
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

<br/>

This example uses **CreateDatabase** to create a new, encrypted **Database** object.

```vb
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
```
