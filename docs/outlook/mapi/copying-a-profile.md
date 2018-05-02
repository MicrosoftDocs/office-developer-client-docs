---
title: "Copying a Profile"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b722a157-0d92-404d-9075-39547241dbb7
description: "Last modified: July 23, 2011"
 
 
---

# Copying a Profile

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
One way to create a profile is to copy from an existing profile and alter the necessary message services and service providers. Copying a profile involves using a profile administration object, provided by MAPI through the [MAPIAdminProfiles](mapiadminprofiles.md) function. 
  
 **To copy a profile**
  
1. Call **MAPIAdminProfiles** to retrieve an **IProfAdmin** interface pointer. 
    
2. Call [IProfAdmin::GetProfileTable](iprofadmin-getprofiletable.md) to access the profile table. 
    
3. Build a property restriction with an [SPropertyRestriction](spropertyrestriction.md) structure to match **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) with the name of the profile to be copied. 
    
4. Call [IMAPITable::FindRow](imapitable-findrow.md) to locate the appropriate row in the profile table. 
    
5. Call [IProfAdmin::CopyProfile](iprofadmin-copyprofile.md), passing the value of the **PR_DISPLAY_NAME** column as the  _lpszOldProfileName_ parameter. 
    

