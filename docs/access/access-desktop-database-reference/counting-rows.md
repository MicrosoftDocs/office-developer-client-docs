---
title: Counting Rows
TOCTitle: Counting Rows
ms:assetid: ff684c5e-7f41-0dae-beea-f5c71f79bd84
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ250312(v=office.15)
ms:contentKeyID: 48548963
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Counting Rows


_**Applies to:** Access 2013 | Office 2013_

The **RecordCount** property returns a **Long** value that indicates the number of records in the **Recordset**. Use the **RecordCount** property to find out how many records are in a **Recordset** object. The property returns -1 when ADO cannot determine the number of records or if the provider or cursor type does not support **RecordCount**. Reading the **RecordCount** property on a closed **Recordset** causes an error.

The **RecordCount** property depends on the capabilities of the provider and the type of cursor. The **RecordCount** property will return -1 for a forward-only cursor, the actual count for a static or keyset cursor, and either -1 or the actual count for a dynamic cursor, depending on the data source.

The sample **Recordset** introduced in [Examining Data](chapter-3-examining-data.md) would return –1 because a forward-only cursor was opened. In order to use the **RecordCount** property, you would need to open the **Recordset** with a more sophisticated cursor (static or keyset).

In certain cases, your provider or cursor might be unable to provide the **RecordCount** value without first fetching all records from the data source. To force this type of fetch, call the **Recordset** **MoveLast** method before calling **RecordCount**.

If you were to replace the line of code that calls the **Recordset** **Open** method with the following:

``` 
 
oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText 
```

you would be able to use the **RecordCount** property because static cursors with the [Microsoft OLE DB Provider for SQL Server](microsoft-ole-db-provider-for-sql-server.md) support **RecordCount**. For example, the following code would print out the number of records returned by the command to the debug window, assuming the cursor supports the **RecordCount** property:

``` 
 
Debug.Print oRs.RecordCount ' Output: 4 
```

From this point forward, assume that these more capable (but more expensive) cursor and lock type settings are used.

