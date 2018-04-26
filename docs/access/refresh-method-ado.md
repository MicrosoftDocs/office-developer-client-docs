---
title: "Refresh Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: f1c8829f-9c7d-12b6-7470-727ff38d663e

---

# Refresh Method (ADO)

Updates the objects in a collection to reflect objects available from, and specific to, the provider.
  
## Syntax

 *collection*  . **Refresh**
  
## Remarks

The **Refresh** method accomplishes different tasks depending on the collection from which you call it. 
  
## Parameters

Using the **Refresh** method on a [Command](command-object-ado.md) object's [Parameters](parameters-collection-ado.md) collection retrieves provider-side parameter information for the stored procedure or parameterized query specified in the **Command** object. The collection will be empty for providers that do not support stored procedure calls or parameterized queries. 
  
You should set the [ActiveConnection](activeconnection-property-ado.md) property of the **Command** object to a valid [Connection](connection-object-ado.md) object, the [CommandText](commandtext-property-ado.md) property to a valid command, and the [CommandType](commandtype-property-ado.md) property to **adCmdStoredProc** before calling the **Refresh** method. 
  
If you access the **Parameters** collection before calling the **Refresh** method, ADO will automatically call the method and populate the collection for you. 
  
> [!NOTE]
> If you use the **Refresh** method to obtain parameter information from the provider and it returns one or more variable-length data type [Parameter](parameter-object-ado.md) objects, ADO may allocate memory for the parameters based on their maximum potential size, which will cause an error during execution. You should explicitly set the [Size](size-property-ado.md) property for these parameters before calling the [Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx) method to prevent errors. 
  
 **Fields**
  
Using the **Refresh** method on the **Fields** collection has no visible effect. To retrieve changes from the underlying database structure, you must use either the [Requery](requery-method-ado.md) method or, if the [Recordset](recordset-object-ado.md) object does not support bookmarks, the [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) method. 
  
 **Properties**
  
Using the **Refresh** method on a **Properties** collection of some objects populates the collection with the dynamic properties that the provider exposes. These properties provide information about functionality specific to the provider, beyond the built-in properties ADO supports. 
  

