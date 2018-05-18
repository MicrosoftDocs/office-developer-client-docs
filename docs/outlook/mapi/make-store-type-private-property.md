---
title: "Make Store Type Private Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- Make Store Type Private Property
api_type:
- COM
ms.assetid: 7f489f55-46d4-8a88-6ebe-9db6446e69a5
description: "Last modified: March 09, 2015"
---

# Make Store Type Private Property

  
  
**Applies to**: Outlook 
  
Treats a secondary store as private.
  
## Quick info

|||
|:-----|:-----|
|Exposed on:  <br/> |[IMsgStore : IMAPIProp](imsgstoreimapiprop.md) object  <br/> |
|Created by:  <br/> |Store provider  <br/> |
|Accessed by:  <br/> |Outlook and other clients  <br/> |
|Property type:  <br/> |PT_BOOLEAN  <br/> |
|Access type:  <br/> |Read/write  <br/> |
   
## Remarks

To provide any of the store functionality, the store provider must implement [IMsgStore : IMAPIProp](imsgstoreimapiprop.md) and return a valid property tag for any of these properties passed to an [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) call. When the property tag for any of these properties is passed to [IMAPIProp::GetProps](imapiprop-getprops.md), the store provider must also return the correct property value. Store providers can call [HrGetOneProp](hrgetoneprop.md) and [HrSetOneProp](hrsetoneprop.md) to get or set these properties. 
  
To retrieve the value of this property, the client should first use [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) to obtain the property tag, and then specify this property tag in [IMAPIProp::GetProps](imapiprop-getprops.md) to get the value. When calling [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md), specify the following values for the [MAPINAMEID](mapinameid.md) structure pointed at by the input parameter  _lppPropNames_:
  
|||
|:-----|:-----|
|lpGuid:  <br/> |PS_PUBLIC_STRINGS  <br/> |
|ulKind:  <br/> |MNID_STRING  <br/> |
|Kind.lpwstrName:  <br/> |L"urn:schemas-microsoft-com:office:outlook#storetypeprivate"  <br/> |
   
A store provider can use this property to have Outlook treat it as private when it is a secondary store for a user. 
  
By default, Outlook treats a secondary store the same way as a delegate store, and items in the secondary store are private only if the user marks them specifically as private. When this property is **true**, items deleted from a secondary store are moved to the **Deleted Items** folder in the primary store. Items marked private are not displayed. Drafts are stored in the Drafts folder in the primary store. 
  
This property is ignored if the version of Outlook is earlier than Microsoft Office Outlook 2003 Service Pack 1, or if its value is **false**.
  

