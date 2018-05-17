---
title: "Profile Tables"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: cd8d60df-98fb-4e08-b547-0836bb31be79
description: "Last modified: July 23, 2011"
 
 
---

# Profile Tables

  
  
**Applies to**: Outlook 
  
The profile table lists information about all profiles associated with a particular client application. There is one profile table for every session, implemented by MAPI for use by clients. 
  
Clients access the profile table by calling the [IProfAdmin::GetProfileTable](iprofadmin-getprofiletable.md) method. 
  
The profile table is a static table. Profiles that have been marked for deletion are not included in the profile table.
  
As with most table implementations, if **GetProfileTable** is called and there are no profiles available to the client, the table is created with zero rows. 
  
The following properties make up the required column set in profile tables:
  
 **PR_DEFAULT_PROFILE** ( [PidTagDefaultProfile](pidtagdefaultprofile-canonical-property.md)) 
  
 **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) 
  
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

