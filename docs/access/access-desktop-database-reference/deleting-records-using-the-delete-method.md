﻿---
title: Deleting Records Using the Delete Method
TOCTitle: Deleting Records Using the Delete Method
ms:assetid: 22917c33-4d14-ebab-d85c-2cbe7f68c560
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249003(v=office.15)
ms:contentKeyID: 48543708
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Deleting Records Using the Delete Method


**Applies to**: Access 2013 | Office 2013

Using the **Delete** method marks the current record or a group of records in a **Recordset** object for deletion. If the **Recordset** object does not allow record deletion, an error occurs. If you are in immediate update mode, deletions occur in the database immediately. If a record cannot be successfully deleted (due to database integrity violations, for example), the record will remain in edit mode after the call to **Update**. This means that you must cancel the update using [CancelUpdate](cancelupdate-method-ado.md) before moving off the current record (for example, using [Close](close-method-ado.md), [Move](move-method-ado.md), or [NextRecordset](nextrecordset-method-ado.md)).

If you are in batch update mode, the records are marked for deletion from the cache and the actual deletion happens when you call the **UpdateBatch** method. (To view the deleted records, set the **Filter** property to **adFilterAffectedRecords** after **Delete** is called.)

Attempting to retrieve field values from the deleted record generates an error. After deleting the current record, the deleted record remains current until you move to a different record. Once you move away from the deleted record, it is no longer accessible.

If you nest deletions in a transaction, you can recover deleted records by using the **RollbackTrans** method. If you are in batch update mode, you can cancel a pending deletion or group of pending deletions by using the **CancelBatch** method.

If the attempt to delete records fails because of a conflict with the underlying data (for example, a record has already been deleted by another user), the provider returns warnings to the **Errors** collection but does not halt program execution. A run-time error occurs only if there are conflicts on all the requested records.

If the **Unique Table** dynamic property is set and the **Recordset** is the result of executing a JOIN operation on multiple tables, the **Delete** method will delete rows only from the table named in the **Unique Table** property.

The **Delete** method takes an optional argument that allows you to specify which records are affected by the **Delete** operation. The only valid values for this argument are either of the following ADO **AffectEnum** enumerated constants:

  - **adAffectCurrent**Affects only the current record.

  - **adAffectGroup**Affects only records that satisfy the current **Filter** property setting. The **Filter** property must be set to a **FilterGroupEnum** value or an array of **Bookmarks** to use this option.

The following code shows an example of specifying **adAffectGroup** when calling the **Delete** method. This example adds some records to the sample **Recordset** and updates the database. Then it filters the **Recordset** using the **adFilterAffectedRecords** filter enumerated constant, which leaves only the newly added records visible in the **Recordset**. Finally, it calls the **Delete** method and specifies that all of the records that satisfy the current **Filter** property setting (the new records) should be deleted.

``` 
 
'BeginDeleteGroup 
 'add some bogus records 
 With objRs1 
 For i = 0 To 8 
 .AddNew 
 .Fields("CompanyName") = "Shipper Number " & i + 1 
 .Fields("Phone") = "(425) 555-000" & (i + 1) 
 .Update 
 Next i 
 
 're-connect & update 
 .ActiveConnection = GetNewConnection 
 .UpdateBatch 
 
 'filter on newly added records 
 .Filter = adFilterAffectedRecords 
 Debug.Print "Deleting the " & .RecordCount & _ 
 " records you just added." 
 
 'delete the newly added bogus records 
 .Delete adAffectGroup 
 .Filter = adFilterNone 
 Debug.Print .RecordCount & " records remain." 
 
 .Close 
 End With 
'EndDeleteGroup 
```

