---
title: "CrawlSourceSupportMask"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- CrawlSourceSupportMask
api_type:
- COM
ms.assetid: d0a2f7ea-df6a-89e8-18c2-ac92e0a20edc
description: "Last modified: March 09, 2015"
---

# CrawlSourceSupportMask

  
  
**Applies to**: Outlook 
  
Specifies whether Microsoft Office Outlook should scan folders in a store, including Contacts, Calendar, and Tasks folders, on startup to populate the Navigation Pane.
  
## Quick Info

|||
|:-----|:-----|
|Exposed on:  <br/> |[IMsgStore : IMAPIProp](imsgstoreimapiprop.md) object  <br/> |
|Created by:  <br/> |Store provider  <br/> |
|Accessed by:  <br/> |Outlook and other clients  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Access type:  <br/> |Read-only or read/write depending on the store provider  <br/> |
   
## Remarks

To provide any of the store functionality, the store provider must implement [IMAPIProp : IUnknown](imapipropiunknown.md) and return a valid property tag for any of these properties passed to an [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) call. When the property tag for any of these properties is passed to [IMAPIProp::GetProps](imapiprop-getprops.md), the store provider must also return the correct property value. Store providers can call [HrGetOneProp](hrgetoneprop.md) and [HrSetOneProp](hrsetoneprop.md) to get or set these properties. 
  
To retrieve the value of this property, the client should first use [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) to obtain the property tag, and then specify this property tag in [IMAPIProp::GetProps](imapiprop-getprops.md) to get the value. When calling [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md), specify the following values for the [MAPINAMEID](mapinameid.md) structure pointed at by the input parameter  _lppPropNames_:
  
|||
|:-----|:-----|
|lpGuid:  <br/> |PSETID_Common  <br/> |
|ulKind:  <br/> |MNID_STRING  <br/> |
|Kind.lpwstrName:  <br/> |L"CrawlSourceSupportMask"  <br/> |
   
This property provides a way for store providers to specify whether Outlook should scan various folders in a store. It is used on startup when Outlook scans existing folders on each opened store to populate the **Navigation** pane; Outlook checks for the presence and value of this property on a store before initiating the scan. 
  
By default, this property is not exposed on a store, which means Outlook can scan folders on the store. If the property is exposed, the following are the possible values:
  
```
enum { 
 CSM_DEFAULT              = 0, 
 CSM_DO_NOT_CRAWL         = 1 << 0x0, 
 CSM_CLIENT_DO_NOT_CHANGE = 1 << 0xF 
};
```

CSM_DEFAULT
  
- Outlook can scan folders on the store.
    
CSM_DO_NOT_CRAWL
  
- Outlook should not scan folders on the store.
    
CSM_CLIENT_DO_NOT_CHANGE
  
- Do not allow clients to change this property on the store. Note that the constant **CSM_CLIENT_DO_NOT_CHANGE** is for future reference and is not currently implemented. For now, a store can prevent clients from changing this flag by hardcoding the value that the store returns for this property. 
    

