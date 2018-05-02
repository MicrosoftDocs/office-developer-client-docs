---
title: "MAPI Profiles"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 493c87a4-317d-47ec-850b-342cac59594b
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Profiles

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
A profile stores information about service providers and message services that are installed on a computer. For every session, a client at logon time selects one profile that describes the providers and services to be used. A client can choose from a collection of profiles and, if desired, establish one as the default. The default profile is the profile that is selected automatically when a client starts a session and has not explicitly specified a profile.
  
Also in these topics, you will find a discussion of the nickname cache, which is stored in a binary stream.
  
- [Nickname cache](nickname-cache.md)
    
- [Autocomplete Stream](autocomplete-stream.md)
    
- [Binary File Parsing](http://portalvhds6gyn3khqwmgzd.blob.core.windows.net/files/NK2/NK2WithBinaryExample.pdf)
    
## Profile Sections

Profiles are divided into sections that clients and service providers access to display profile properties to users or to make configuration changes. A profile section is a MAPI object that implements the **IProfSect** interface, an interface that derives from **IMAPIProp** and has no additional methods. For more information, see [IProfSect : IMAPIProp](iprofsectimapiprop.md). Its only purpose is to manipulate the properties of a profile section. To retrieve an **IProfSect** pointer to a particular profile section, clients and service providers call the following methods. 
  
|||
|:-----|:-----|
|Clients can call:  <br/> |[IMAPISession::OpenProfileSection](imapisession-openprofilesection.md) <br/> |
|Service providers can call:  <br/> |[IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) <br/> |
|Either clients or providers can call:  <br/> |[IProviderAdmin::OpenProfileSection](iprovideradmin-openprofilesection.md) <br/> |
   
Profiles are organized hierarchically much like the MAPISVC.INF file. At the top of the hierarchy, there are profile sections that contain information relevant to the profile. The middle level includes sections that contain information about a particular message service and the lower level includes sections that contain information about one of the service providers in a message service. 
  
Every profile has several required properties that are stored in one or more of the sections of the profile. For example, every profile has the **PR_PROFILE_NAME** ( [PidTagProfileName](pidtagprofilename-canonical-property.md)) and **PR_SEARCH_KEY** ( [PidTagSearchKey](pidtagsearchkey-canonical-property.md)) properties. A profile's search key is set to the value defined in MAPIGUID.H as MUID_PROFILE_INSTANCE and is always guaranteed to be unique among all profiles. Although two profiles can have the same name, they cannot have the same search key. Search keys should be treated as binary data instead of data of any particular type.
  
Message store providers are required to include their message store's **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property in the profile sections for the profile and for their message store provider and to keep these entries synchronized. When a message store is created, the provider sets **PR_DISPLAY_NAME** based on the value stored in these profile sections. 
  
There are two major differences between profile sections and other objects that inherit from **IMAPIProp**: 
  
- Profile sections do not support transactions.
    
- Profile sections do not support named properties, returning MAPI_E_NO_SUPPORT from their **IMAPIProp::GetIDsFromNames** and **IMAPIProp::GetNamesFromIDs** implementations. For more information, see [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) and [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md).
    
Because profile sections do not support transactions, any changes made with calls to **IMAPIProp::CopyProps**, **CopyTo**, or **SetProps** immediately take effect. For more information, see [IMAPIProp::CopyProps](imapiprop-copyprops.md). Clients and service providers can call a profile section's **IMAPIProp::SaveChanges** method and it will succeed, but it does not affect the profile section data. For more information, see [IMAPIProp::SaveChanges](imapiprop-savechanges.md). Having changes occur immediately can affect how service providers implement the property sheets that clients use to display profile properties to users. Service providers that want users to be able to postpone or undo changes must implement their property sheets with copies of profile sections instead of the real sections. By using copies, users can make changes and then later cancel those changes, leaving the original profile sections untouched. 
  
The order in which information appears in a profile affects how MAPI configures resources and makes assignments in a session. The following assignments are affected by profile order:
  
- Default message store
    
- Personal address book
    
- Default message store search path
    
- Default address book search path
    
- Transport provider order
    
MAPI sets the default message store to be the first message store in the profile that has the STATUS_DEFAULT_STORE flag set in its **PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) property, which indicates that it can be the default store. Clients can override this setting by calling **IMAPISession::SetDefaultStore**. For more information, see [IMAPISession::SetDefaultStore](imapisession-setdefaultstore.md).
  
MAPI creates a transport order for handling outgoing and incoming messages. When more than one transport provider has registered for a message of a particular type, MAPI uses this order to determine which provider should handle the message. MAPI sets the transport order to be the order in which the transport providers were added to the profile with one exception--the transports that set the STATUS_XP_PREFER_LAST flag in their **PR_RESOURCE_FLAGS** property are positioned last in the order. Clients can set the transport order by calling **IMsgServiceAdmin::MsgServiceTransportOrder**. For more information, see [IMsgServiceAdmin::MsgServiceTransportOrder](imsgserviceadmin-msgservicetransportorder.md).
  
These guidelines for ordering service providers and message services might sometimes conflict. If there is a conflict, your code should resolve the conflict. You can use the Mail Control Panel program to inspect a profile that you have created to determine whether the providers have been configured as expected.
  

