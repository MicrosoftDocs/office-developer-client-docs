---
title: "Deleting a Profile"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4d01ab2e-40fd-409d-a69d-163b7d5462ca
description: "Last modified: July 23, 2011"
 
 
---

# Deleting a Profile

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
 **To delete a profile**
  
- Call [IProfAdmin::DeleteProfile](iprofadmin-deleteprofile.md).
    
 **DeleteProfile** marks the profile for deletion if it is currently being used, waiting until it is no longer active to remove it. The profile does not actually disappear until every client with an active session has disconnected. 
  
 **DeleteProfile** calls the entry point function of every message service in the profile with the  _ulContext_ parameter set to MSG_SERVICE_DELETE. The calls to the entry point functions occur before the services are physically removed from the profile. 
  

