---
title: "Finding a Profile Name"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 18df25b7-16b7-44cd-a9a0-5276966c1fd4
description: "Last modified: July 23, 2011"
---

# Finding a Profile Name

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Clients sometimes need to find the name of the profile currently being used for the session, the name of the default profile, or the name of an alternate profile installed on the computer.
  
There are a few ways to retrieve the name of a profile during the course of a session. If you need to find the name of a profile that is not necessarily the one being used for the session, use the first procedure. If you need to find the name of the default profile, use the second procedure. If you need to find the name of the current profile for the session, use the last procedure. 
  
 **To find the name of any profile**
  
1. Call [MAPIAdminProfiles](mapiadminprofiles.md) to retrieve an **IProfAdmin** interface pointer. 
    
2. Call [IProfAdmin::GetProfileTable](iprofadmin-getprofiletable.md) to access the profile table. 
    
3. Call the profile table's [IMAPITable::QueryRows](imapitable-queryrows.md) method to retrieve all of the rows in the table and examine each one to determine if it represents your target profile. 
    
 **To find the name of the default profile**
  
1. Call [MAPIAdminProfiles](mapiadminprofiles.md).
    
2. Call [IProfAdmin::GetProfileTable](iprofadmin-getprofiletable.md) to access the profile table. 
    
3. Build a property restriction with an [SPropertyRestriction](spropertyrestriction.md) structure to match **PR_DEFAULT_PROFILE** ( [PidTagDefaultProfile](pidtagdefaultprofile-canonical-property.md)) with the value TRUE.
    
4. Call [IMAPITable::FindRow](imapitable-findrow.md) to locate the row in the profile table that represents the default profile. The **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) column contains the name of the default profile.
    
 **To find the name of the current profile**
  
To find the name of the current profile, complete one of the following steps:
  
- Assuming that you have the [MAPIUID](mapiuid.md) structure representing one of the current profile's sections, pass it in the  _lpUID_ parameter to [IMAPISession::OpenProfileSection](imapisession-openprofilesection.md). Retrieve the profile section's **PR_PROFILE_NAME** ( [PidTagProfileName](pidtagprofilename-canonical-property.md)) property using its [IMAPIProp::GetProps](imapiprop-getprops.md) method. 
    
- Call [IMAPISession::GetStatusTable](imapisession-getstatustable.md) to access the status table and find the row that has its **PR_RESOURCE_TYPE** ( [PidTagResourceType](pidtagresourcetype-canonical-property.md)) column set to MAPI_SUBSYSTEM. The **PR_DISPLAY_NAME** column for this row is the profile name. Do not use the status table during start up because it blocks an application until the MAPI spooler has finished initializing all of the transport providers. This can degrade your performance. 
    

