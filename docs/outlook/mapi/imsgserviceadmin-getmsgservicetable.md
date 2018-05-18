---
title: "IMsgServiceAdminGetMsgServiceTable"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMsgServiceAdmin.GetMsgServiceTable
api_type:
- COM
ms.assetid: 064dd5ca-0108-4045-b17b-0bb29cb93346
description: "Last modified: March 09, 2015"
---

# IMsgServiceAdmin::GetMsgServiceTable

  
  
**Applies to**: Outlook 
  
Provides access to the message service table, a list of the message services in the profile.
  
```cpp
HRESULT GetMsgServiceTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] Always NULL.
    
 _lppTable_
  
> [out] A pointer to a pointer to the message service table.
    
## Return value

S_OK 
  
> The message service table was successfully returned.
    
## Remarks

The **IMsgServiceAdmin::GetMsgServiceTable** method provides access to the message service table, a table that MAPI maintains that lists the message services currently installed in the session profile. For a complete list of columns in the message service table, see [Message Service Table](message-service-tables.md).
  
The message service table is static. After a client has been given access to it, subsequent message service additions or deletions will not affect it. If there are no message services in the current profile, **GetMsgServiceTable** returns a table with zero rows. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MsgServiceTableDlg.cpp  <br/> |CMsgServiceTableDlg::OnRefreshView  <br/> |MFCMAPI uses the **IMsgServiceAdmin::GetMsgServiceTable** method to load the table of services in a profile to render in the view.  <br/> |
   
## See also



[IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md)
  
[IMsgServiceAdmin::DeleteMsgService](imsgserviceadmin-deletemsgservice.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

