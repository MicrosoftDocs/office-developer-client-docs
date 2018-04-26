---
title: "Adding Data to a Recordset"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: a3d121a8-f52f-66cd-8849-c3a75aeb276a
description: "The Recordset is probably the most used of the ADO objects. In ADO a Recordset is best thought of as the combination of a result set from a data source and its associated cursor behaviors. Thus, you can put data into a Recordset and then use the Recordset methods and properties to navigate through the rows of data, view the values in the rows, and otherwise manipulate the result set."
---

# Adding Data to a Recordset

The **Recordset** is probably the most used of the ADO objects. In ADO a **Recordset** is best thought of as the combination of a result set from a data source and its associated cursor behaviors. Thus, you can put data into a **Recordset** and then use the **Recordset** methods and properties to navigate through the rows of data, view the values in the rows, and otherwise manipulate the result set. 
  
This section will focus on adding data to the **Recordset**. For information about navigating through the data or updating the data, see [Chapter 4: Editing Data](chapter-4-editing-data.md) and [Chapter 5: Updating and Persisting Data](chapter-5-updating-and-persisting-data.md). You do not always need the advanced capabilities of a **Command** object to add your result set to a **Recordset**. Often, you can execute your command by setting the **Source** property on the **Recordset** or passing a command string to the **Recordset** object **Open** method. 
  
There are a variety of ways to add data from your data source to a **Recordset**. The technique you use depends on the needs of your application and the capabilities of your provider. 
  

