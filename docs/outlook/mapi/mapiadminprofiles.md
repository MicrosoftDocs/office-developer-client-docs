---
title: "MAPIAdminProfiles"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPIAdminProfiles
api_type:
- HeaderDef
ms.assetid: 82a9e379-39e4-4257-8cba-a6758f431cdc
description: "Last modified: March 09, 2015"
---

# MAPIAdminProfiles

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates a profile administration object. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
HRESULT MAPIAdminProfiles(
  ULONG ulFlags,
  LPPROFADMIN FAR * lppProfAdmin
);
```

## Parameters

 _ulFlags_
  
> [in] Bitmask of flags indicating options for the service entry function. 
    
 _lppProfAdmin_
  
> [out] Pointer to a pointer to the new profile administration object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIObjects.cpp  <br/> |CMapiObjects::GetProfAdmin  <br/> |MFCMAPI uses the **MAPIAdminProfiles** method to get the profile administration object.  <br/> |
   
## See also



[IProfAdmin::CreateProfile](iprofadmin-createprofile.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

