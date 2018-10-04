---
title: 'Sending the Updates: UpdateBatch'
TOCTitle: 'Sending the Updates: UpdateBatch'
ms:assetid: a840b9a7-7ccd-9c31-7951-8921dadf381e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249778(v=office.15)
ms:contentKeyID: 48546898
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Sending the Updates: UpdateBatch


_**Applies to:** Access 2013 | Office 2013_

## Sending the Updates: UpdateBatch Method

The following code opens a **Recordset** in batch mode by setting the **LockType** property to **adLockBatchOptimistic** and the **CursorLocation** to **adUseClient**. It adds two new records and changes the value of a field in an existing record, saving the original values, and then calls **UpdateBatch** to send the changes back to the data source.

``` 
 
'BeginBatchUpdate 
    strSQL = "SELECT ShipperId, CompanyName, Phone FROM Shippers" 
                  
    objRs1.CursorLocation = adUseClient 
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText 
     
    ' Change value of Phone field for first record in Recordset, saving value 
    ' for later restoration. 
    intId = objRs1("ShipperId") 
    strPhone = objRs1("Phone") 
     
    objRs1("Phone") = "(111) 555-1111" 
     
    'Add two new records 
    For i = 0 To 1 
        objRs1.AddNew 
        objRs1(1) = "New Shipper #" & CStr((i + 1)) 
        objRs1(2) = "(nnn) 555-" & i & i & i & i 
    Next i 
     
    ' Send the updates 
    objRs1.UpdateBatch 
'EndBatchUpdate 
```

If you are editing the current record or adding a new record when you call the **UpdateBatch** method, ADO will automatically call the **Update** method to save any pending changes to the current record before transmitting the batched changes to the provider.

