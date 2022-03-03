---
title: "ITableDataHrNotify"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ITableData.HrNotify
api_type:
- COM
ms.assetid: 98548b50-342e-434a-9ad3-c37ba418c5ce
---

# ITableData::HrNotify

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sends a notification for a table row.
  
```cpp
HRESULT HrNotify(
  ULONG ulFlags,
  ULONG cValues,
  LPSPropValue lpSPropValue
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _cValues_
  
> [in] The count of property values in the [SPropValue](spropvalue.md) structure pointed to by the  _lpSPropValue_ parameter. 
    
 _lpSPropValue_
  
> [in] A pointer to an **SPropValue** structure that describes the values of the columns in the target row. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

The **ITableData::HrNotify** method sends a TABLE_ROW_MODIFIED notification for the row that matches the row described by the properties pointed to by the  _lpSPropValue_ parameter. **HrNotify** sends the notification regardless of whether changes have occurred to the row. All clients and service providers that have views of the table and have called [IMAPITable::Advise](imapitable-advise.md) to register for notifications on their views receive this notification. 
  
## See also



[SPropValue](spropvalue.md)
  
[TABLE_NOTIFICATION](table_notification.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

