---
<<<<<<< HEAD
title: CacheSize Property (ADO)
TOCTitle: CacheSize Property (ADO)
=======
title: CacheSize property (ADO)
TOCTitle: CacheSize property (ADO)
>>>>>>> master
ms:assetid: 42f86cc0-30dc-669b-9e65-5e7ecd52c4d7
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249200(v=office.15)
ms:contentKeyID: 48544491
ms.date: 09/18/2015
mtps_version: v=office.15
---

<<<<<<< HEAD
# CacheSize Property (ADO)
=======
# CacheSize property (ADO)
>>>>>>> master


**Applies to**: Access 2013 | Office 2013

Indicates the number of records from a [Recordset](recordset-object-ado.md) object that are cached locally in memory.

<<<<<<< HEAD
## Settings and Return Values
=======
## Settings and return values
>>>>>>> master

Sets or returns a **Long** value that must be greater than 0. Default is 1.

## Remarks

Use the **CacheSize** property to control how many records to retrieve at one time into local memory from the provider. For example, if the **CacheSize** is 10, after first opening the **Recordset** object, the provider retrieves the first 10 records into local memory. As you move through the **Recordset** object, the provider returns the data from the local memory buffer. As soon as you move past the last record in the cache, the provider retrieves the next 10 records from the data source into the cache.


> [!NOTE]
> <P><STRONG>CacheSize</STRONG> is based on the <STRONG>Maximum Open Rows</STRONG> provider-specific property (in the <STRONG>Properties</STRONG> collection of the <STRONG>Recordset</STRONG> object). You cannot set <STRONG>CacheSize</STRONG> to a value greater than <STRONG>Maximum Open Rows</STRONG>. To modify the number of rows which can be opened by the provider, set <STRONG>Maximum Open Rows</STRONG>.</P>



The value of **CacheSize** can be adjusted during the life of the **Recordset** object, but changing this value only affects the number of records in the cache after subsequent retrievals from the data source. Changing the property value alone will not change the current contents of the cache.

If there are fewer records to retrieve than **CacheSize** specifies, the provider returns the remaining records and no error occurs.

A **CacheSize** setting of zero is not allowed and returns an error.

Records retrieved from the cache don't reflect concurrent changes that other users made to the source data. To force an update of all the cached data, use the [Resync](resync-method-ado.md) method.

If **CacheSize** is set to a value greater than one, the navigation methods ([Move](move-method-ado.md), [MoveFirst, MoveLast, MoveNext, and MovePrevious](movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) may result in navigation to a deleted record, if deletion occurs after the records were retrieved. After the initial fetch, subsequent deletions will not be reflected in your data cache until you attempt to access a data value from a deleted row. However, setting **CacheSize** to one eliminates this issue since deleted rows cannot be fetched.

