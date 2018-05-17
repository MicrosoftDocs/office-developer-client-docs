---
title: "Creating a Profile by Using Custom Code"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 5632cd25-58f5-4b9c-906c-cd377abc3daf
description: "Last modified: July 23, 2011"
 
 
---

# Creating a Profile by Using Custom Code

  
  
**Applies to**: Outlook 
  
If you choose to write code to create a profile, make sure that you understand how to order profile entries and the type and amount of information that is needed for each entry. The implications of ordering entries in a profile is explained in [MAPI Profiles](mapi-profiles.md).
  
 **To create a profile with C or C++ code**
  
1. Read the header file for each message service. Understand what properties you will need to configure and what values you will use.
    
2. Call the [MAPIAdminProfiles](mapiadminprofiles.md) function to retrieve an **IProfAdmin** interface pointer. 
    
3. Call [IProfAdmin::CreateProfile](iprofadmin-createprofile.md) to create your profile. If you want to create a profile with the message services listed in the **[Default Services]** section of the MAPISVC.INF file, set the MAPI_DEFAULT_SERVICE flag. If you want to enable the user to enter configuration information, set the MAPI_DIALOG flag. Make sure that you set this flag if not all of the necessary information is available through the MAPISVC.INF file. **CreateProfile** calls the entry point function for each message service to be added to the profile with MSG_SERVICE_CREATE set as the  _ulContext_ parameter. 
    
4. Call [IProfAdmin::AdminServices](iprofadmin-adminservices.md) to obtain a message service administration object. 
    
5. Use the message service administration object to add message services to the profile. For each message service that you want to add:
    
1. Call the [IMsgServiceAdmin::CreateMsgService](imsgserviceadmin-createmsgservice.md) method to create the new message service. 
    
2. Call [IMsgServiceAdmin::ConfigureMsgService](imsgserviceadmin-configuremsgservice.md), passing the **MAPIUID** structure of the service you just created and a property value array with its configuration properties. 
    
6. To retrieve the identifier of a newly added service, which is its **PR_SERVICE_UID** ( [PidTagServiceUid](pidtagserviceuid-canonical-property.md)) property, call [IMsgServiceAdmin::GetMsgServiceTable](imsgserviceadmin-getmsgservicetable.md) to access the message service table and search for the row that represents the message service. The last row in the table will represent the most recently added message service. 
    
To make a new profile temporary, call the [IProfAdmin::DeleteProfile](iprofadmin-deleteprofile.md) method immediately after you log on. **DeleteProfile** will mark the new profile as deleted while making it usable for the duration of the session. Because it will not be included in the session's profile table, other clients will be unable to use it. 
  

