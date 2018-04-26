---
title: "Filtering for Updated Records"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0dc22b0a-3501-078d-788c-40aa97f2e644

---

# Filtering for Updated Records

## Filtering for Updated Records

Before you call **UpdateBatch**, you can use the **Recordset** **Filter** property to view only those records which have been changed since the **Recordset** was opened or the last call to **UpdateBatch**. To do this, set **Filter** equal to **adFilterPendingRecords** to determine how many records will be updated, as shown below. 
  
This example extends the previous **UpdateBatch** example by filtering the **Recordset** just before calling the **UpdateBatch**, showing the user which records will change and allowing her to cancel the update (using the **CancelBatch** method). 
  
```
 
'BeginFilterAffected 
    objRs1.Filter = adFilterPendingRecords 
    objRs1.MoveFirst 
     
    strMsg = "The following " &amp; objRs1.RecordCount &amp; " values will " &amp; _ 
             "be updated. Do you wish to proceed?" 
    While Not objRs1.EOF 
        strMsg = strMsg &amp; vbCrLf &amp; objRs1(0) &amp; vbTab &amp; objRs1(1) &amp; vbTab &amp; _ 
                 objRs1(2) &amp; vbCrLf 
        objRs1.MoveNext 
    Wend 
     
    blnResp = MsgBox(strMsg, vbYesNo, "Proceed with Update?") 
    If blnResp = True Then 
        objRs1.UpdateBatch 
    Else 
        objRs1.CancelBatch 
    End If 
'EndFilterAffected 

```


