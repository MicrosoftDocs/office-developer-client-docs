﻿---
title: DBEngine Object (DAO)
TOCTitle: DBEngine Object
ms:assetid: ceaeb505-615e-37ba-4633-27240ef8c5de
ms:mtpsurl: https://msdn.microsoft.com/library/Ff834506(v=office.15)
ms:contentKeyID: 48547792
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DBEngine Object (DAO)


**Applies to**: Access 2013 | Office 2013

The **DBEngine** object is the top level object in the DAO object model.

## Remarks

The **DBEngine** object contains and controls all other objects in the hierarchy of DAO objects. You can't create additional **DBEngine** objects, and the **DBEngine** object isn't an element of any collection.

With any type of database or connection, you can:

  - Use the **Version** property to obtain the DAO version number.

  - Use the **LoginTimeout** property to obtain or set the ODBC login timeout, and the **RegisterDatabase** method to provide ODBC information to the Microsoft Access database engine.

  - Use the **DefaultPassword** and **DefaultUser** properties to set the user identification and password for the default **Workspace** object.

  - Use the **CreateWorkspace** method to create a new **Workspace** object. You can use optional arguments to override the settings of the **DefaultType**, **DefaultPassword**, and **DefaultUser** properties.

  - Use the **OpenDatabase** method to open a database in the default **Workspace**, and use the **BeginTrans**, **Commit**, and **Rollback** methods to control transactions on the default **Workspace**.

  - Use the **Workspaces** collection to reference specific **Workspace** objects.

  - Use the **Errors** collection to examine data access error details.

Other properties and methods are only available when you use DAO with the Microsoft Access database engine. You can use them to control the Microsoft Access database engine, manipulate its properties, and perform tasks on temporary objects that aren't elements of collections. For example, you can:

  - Use the **CreateDatabase** method to create a new Microsoft Access database engine **Database** object.

  - Use the **Idle** method to enable the Microsoft Access database engine to complete any pending tasks.

  - Use the **CompactDatabase** and **RepairDatabase** methods to maintain database files.

  - Use the **IniPath** and **SystemDB** properties to specify the location of Microsoft Access database engine Windows Registry information and the Microsoft Access workgroup information file, respectively. The **SetOption** method allows you override windows registry settings for the Microsoft Access database engine.

After you change the **DefaultType** and **IniPath** property settings, only subsequent **Workspace** objects will reflect these changes.

To refer to a collection that belongs to the **DBEngine** object, or to refer to a method or property that applies to this object, use this syntax:

\[**DBEngine**.\]\[collection | method | property\]

## Example

This example enumerates the collections of the **DBEngine** object.

    Sub DBEngineX() 
     
     Dim wrkLoop As Workspace 
     Dim prpLoop As Property 
     
     With DBEngine 
     Debug.Print "DBEngine Properties" 
     
     ' Enumerate Properties collection of DBEngine, 
     ' trapping for properties whose values are 
     ' invalid in this context. 
     For Each prpLoop In .Properties 
     On Error Resume Next 
     Debug.Print " " & prpLoop.Name & " = " _ 
     & prpLoop 
     On Error GoTo 0 
     Next prpLoop 
     
     Debug.Print "Workspaces collection of DBEngine" 
     
     ' Enumerate Workspaces collection of DBEngine. 
     For Each wrkLoop In .Workspaces 
     Debug.Print " " & wrkLoop.Name 
     
     ' Enumerate Properties collection of each 
     ' Workspace object, trapping for properties 
     ' whose values are invalid in this context. 
     For Each prpLoop In wrkLoop.Properties 
     On Error Resume Next 
     Debug.Print " " & prpLoop.Name & _ 
     " = " & prpLoop 
     On Error GoTo 0 
     Next prpLoop 
     
     Next wrkLoop 
     
     End With 
     
    End Sub

