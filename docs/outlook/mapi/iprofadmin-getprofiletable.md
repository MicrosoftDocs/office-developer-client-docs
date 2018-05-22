---
title: "IProfAdminGetProfileTable"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProfAdmin.GetProfileTable
api_type:
- COM
ms.assetid: cebccd2d-8215-486e-9964-7fc42412cec6
description: "Last modified: March 09, 2015"
---

# IProfAdmin::GetProfileTable

  
  
**Applies to**: Outlook 
  
Provides access to the profile table, a table that contains information about all of the available profiles.
  
```cpp
HRESULT GetProfileTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] Always NULL.
    
 _lppTable_
  
> [out] A pointer to a pointer to the profile table.
    
## Return value

S_OK 
  
> The profile table was successfully retrieved.
    
## Remarks

The **IProfAdmin::GetProfileTable** method provides access to the profile table, which contains one row for every available profile. There are only two columns in each row: the profile's display name, and a flag that indicates whether the profile is the default. 
  
Profiles that have been deleted, or that are in use but have been marked for deletion, are not included in the profile table. The profile table is static; subsequent additions and deletions of profiles are not reflected in the table. 
  
If no profiles exist, **GetProfileTable** returns a table with zero rows. 
  
For more information about the profile table, see [Profile Tables](profile-tables.md). 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MainDlg.cpp  <br/> |CMainDlg::OnShowProfiles  <br/> |MFCMAPI uses the **IProfAdmin::GetProfileTable** method to get the profile table to display in a new dialog box.  <br/> |
   
## See also



[IMAPITable : IUnknown](imapitableiunknown.md)
  
[MAPILogonEx](mapilogonex.md)
  
[IProfAdmin : IUnknown](iprofadminiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

