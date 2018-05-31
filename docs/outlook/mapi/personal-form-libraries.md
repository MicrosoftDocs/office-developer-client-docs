---
title: "Personal Form Libraries"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 6ffcd93c-3737-4342-9cd0-2ca7c0fba52c
description: "Last modified: July 23, 2011"
 
 
---

# Personal Form Libraries

  
  
**Applies to**: Outlook 
  
As its name suggests, personal form libraries contain forms of interest to a particular user. A user's personal form library is the form library associated with the default message store identified in the user's profile; each profile installed on a workstation can use a separate default store, and therefore, a separate personal form library. A personal form library can contain copies of forms that are also contained in other form libraries in addition to other forms.
  
A personal form library is implemented in the associated-contents table of the root folder in a user's default message store — whether that resides on a server or locally on the user's workstation is immaterial. If the user's default message store is stored on the user's workstation, personal form libraries offer enhanced performance by enabling applications to access forms locally instead of over the network. It also makes forms available to users working offline, which can occur when users want to take their forms with them on portable computers and are without access to a network.
  
The properties and underlying implementation of personal form library entries include a "Container ID" property that identifies a master container that the local entry must be synchronized with. This can be the identifier of an arbitrary folder that contains forms. This is useful if you are using a custom form manager that supports some sort of organization-wide form library; the form manager would take care of synchronizing the forms stored in the personal form library and the organization-wide form library. This would probably happen when the form manager was loaded, but could theoretically happen at any time.
  
## See also



[MAPI Forms](mapi-forms.md)

