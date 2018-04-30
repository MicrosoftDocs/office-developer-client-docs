---
title: "Administering Profiles and Message Services"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 89a2ac43-9601-47fc-b736-db48585fe879
description: "Last modified: July 23, 2011"
---

# Administering Profiles and Message Services

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Profile and message service administration can involve creating new profiles, deleting old profiles, and modifying the contents of existing profiles by changing the message services and service providers contained within them. Not all clients support profile and message service administration as standard features. Some clients have nothing more to do with profiles than allow their users to select one at logon time.
  
If you support profile or message service administration, chances are you will use the following interfaces that are implemented by MAPI:
  
- [IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md) to administer a message service in a profile, accessible through either [IMAPISession::AdminServices](imapisession-adminservices.md) or [IProfAdmin::AdminServices](iprofadmin-adminservices.md). Messaging clients typically call **IMAPISession** while configuration clients, or clients that do not send or receive messages, call **IProfAdmin**. Whenever possible, call the **IProfAdmin** method because it does not cause the message service to be started. For more information about using the **IMsgServiceAdmin** interface, see the following topics: [Configuring a Message Service](configuring-a-message-service.md), [Copying a Message Service](copying-a-message-service.md), and [Deleting a Message Service](deleting-a-message-service.md).
    
- [IProfAdmin : IUnknown](iprofadminiunknown.md) to administer a profile, accessible through the [MAPIAdminProfiles](mapiadminprofiles.md) function. For more information about using the **IProfAdmin** interface, see the following topics: [Creating a Profile by Using Custom Code](creating-a-profile-by-using-custom-code.md), [Copying a Profile](copying-a-profile.md), [Deleting a Profile](deleting-a-profile.md), [Finding a Profile Name](finding-a-profile-name.md), and [Setting a Default Profile](setting-a-default-profile.md).
    
- [IProfSect : IMAPIProp](iprofsectimapiprop.md) to maintain the properties in a profile section, accessible through the [IMAPISession::OpenProfileSection](imapisession-openprofilesection.md) or [IProviderAdmin::OpenProfileSection](iprovideradmin-openprofilesection.md) method. For more information about profile sections, see [MAPI Profiles](mapi-profiles.md).
    
- [IProviderAdmin : IUnknown](iprovideradminiunknown.md) to administer the service providers in a message service, accessible through [IMsgServiceAdmin::AdminProviders](imsgserviceadmin-adminproviders.md). For more information about using the **IProviderAdmin** interface, see [Adding or Deleting Providers in a Message Service](adding-or-deleting-providers-in-a-message-service.md).
    
Be careful in your support of profile and message service administration. There are no safeguards to protect against adversely modifying a profile that is in use. MAPI can prevent you from deleting a profile in use, but cannot prevent you from deleting every message service in it. If you delete every message service in a profile, all of the service providers in these services will stop thereby causing unpredictable results to occur.
  
## In This Section

[Creating a Profile](creating-a-profile.md)
  
> Describes how to create a profile.
    
[Copying a Profile](copying-a-profile.md)
  
> Describes how to copy a profile.
    
[Deleting a Profile](deleting-a-profile.md)
  
> Describes how to delete a profile.
    
[Setting a Default Profile](setting-a-default-profile.md)
  
> Describes how to set a default profile.
    
[Finding a Profile Name](finding-a-profile-name.md)
  
> Describes how to find a name of a profile.
    
[Adding a Message Service](adding-a-message-service.md)
  
> Describes how to add a message service.
    
[Configuring a Message Service](configuring-a-message-service.md)
  
> Describes how to configure a message service.
    
[Copying a Message Service](copying-a-message-service.md)
  
> Describes how to copy a message service to a profile.
    
[Deleting a Message Service](deleting-a-message-service.md)
  
> Describes how to delete a message service.
    
[Adding or Deleting Providers in a Message Service](adding-or-deleting-providers-in-a-message-service.md)
  
> Describes how to add or delete providers in a message service.
    

