---
title: "IMAPISupportModifyStatusRow"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.ModifyStatusRow
api_type:
- COM
ms.assetid: a304ca8f-e404-4535-be76-0b673f2061a0
description: "Last modified: July 23, 2011"
---

# IMAPISupport::ModifyStatusRow

  
  
**Applies to**: Outlook 
  
Modifies the status table by adding a new row or modifying an existing row.
  
```
HRESULT ModifyStatusRow(
ULONG cValues,
LPSPropValue lpColumnVals,
ULONG ulFlags
);
```

## Parameters

 _cValues_
  
> [in] The count of properties to be included in the new or modified status table row. 
    
 _lpColumnVals_
  
> [in] A pointer to an array of property values that describe the properties to be included as columns in the new or modified status table row.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how information that defines the status table row is processed. The following flag can be set:
    
STATUSROW_UPDATE 
  
> Directs MAPI to merge the properties included in the array pointed to by  _lpColumnVals_ with an existing status table row, rather than in a new row. 
    
## Return value

S_OK 
  
> The status table was successfully updated.
    
## Remarks

The **IMAPISupport::ModifyStatusRow** method is implemented for all service provider support objects. Service providers call **ModifyStatusRow** at logon time to add a row to the status table and at other times during the session to update the row. **ModifyStatusRow** provides MAPI with the information necessary to build the status table. 
  
## Notes to Callers

Set the STATUSROW_UPDATE flag when you call **ModifyStatusRow** to make changes to the properties in your existing status table row. Doing so informs MAPI that only the columns being changed are passed in the  _lpColumnVals_ parameter. 
  
Clients can use the information in the status table to access your status object. 
  
For a complete list of columns that you should include in your status table row, see [Status Tables](status-tables.md).
  
## See also

#### Reference

[IMAPISupport : IUnknown](imapisupportiunknown.md)

