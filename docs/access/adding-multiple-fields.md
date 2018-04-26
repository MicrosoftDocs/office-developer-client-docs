---
title: "Adding Multiple Fields"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 81b2f9de-4805-4494-9990-09ffda1b2068
description: "Occasionally, it might be more efficient to pass in an array of fields and their corresponding values to the AddNew method, rather than setting Value multiple times for each new field. If FieldList is an array, Values must also be an array with the same number of members; otherwise, an error occurs. The order of field names must match the order of field values in each array. The following code passes an array of fields and an array of values to the AddNew method."
---

# Adding Multiple Fields

Occasionally, it might be more efficient to pass in an array of fields and their corresponding values to the **AddNew** method, rather than setting **Value** multiple times for each new field. If  *FieldList*  is an array,  *Values*  must also be an array with the same number of members; otherwise, an error occurs. The order of field names must match the order of field values in each array. The following code passes an array of fields and an array of values to the **AddNew** method. 
  
```
 
'BeginAddNew2 
 Dim avarFldNames As Variant 
 Dim avarFldValues As Variant 
 
 avarFldNames = Array("CompanyName", "Phone") 
 avarFldValues = Array("Sample Shipper 2", "(931) 555-6334") 
 
 If objRs1.Supports(adAddNew) Then 
 objRs1.AddNew avarFldNames, avarFldValues 
 End If 
 
 'Re-establish a Connection and update 
 Set objRs1.ActiveConnection = GetNewConnection 
 objRs1.UpdateBatch 
'EndAddNew2 

```


