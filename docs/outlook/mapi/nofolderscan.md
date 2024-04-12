---
title: "NoFolderScan"
description: "Describes property information and remarks for NoFolderScan, which specifies whether Microsoft Office Outlook should scan Contacts folders on a store."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 4949aef9-4c96-82cc-cd13-57981e07cc40
---

# NoFolderScan

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies whether Microsoft Office Outlook should scan Contacts folders on a store.
  
## Quick info

|Property|Value|
|:-----|:-----|
|Exposed on:  <br/> |[IMsgStore : IMAPIProp](imsgstoreimapiprop.md) object  <br/> |
|Created by:  <br/> |Store provider  <br/> |
|Accessed by:  <br/> |Outlook and other clients  <br/> |
|Property type:  <br/> |PT_LONG  <br/> |
|Access type:  <br/> |Read-only or read/write depending on the store provider  <br/> |
   
## Remarks

To provide any of the store functionality, the store provider must implement [IMAPIProp : IUnknown](imapipropiunknown.md) and return a valid property tag for any of these properties passed to an [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) call. When the property tag for any of these properties is passed to [IMAPIProp::GetProps](imapiprop-getprops.md), the store provider must also return the correct property value. Store providers can call [HrGetOneProp](hrgetoneprop.md) and [HrSetOneProp](hrsetoneprop.md) to get or set these properties. 
  
To retrieve the value of this property, the client should first use [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) to obtain the property tag, and then specify this property tag in [IMAPIProp::GetProps](imapiprop-getprops.md) to get the value. When calling [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md), specify the following values for the [MAPINAMEID](mapinameid.md) structure pointed at by the input parameter  _lppPropNames_:
  
|Property|Value|
|:-----|:-----|
|lpGuid:  <br/> |PSETID_Common  <br/> |
|ulKind:  <br/> |MNID_STRING  <br/> |
|Kind.lpwstrName:  <br/> |L"NoFolderScan"  <br/> |
   
This property provides a way for store providers to specify to Outlook not to scan Contacts folders in the store to avoid performance degradation. It is used in mail merge operations during which Outlook checks for the presence and value of this property before initiating the scan.
  
By default, this property is not exposed on a store, which means Outlook can scan the Contacts folder on the store. If the property is exposed, the following are the possible values:
  
- Zero (0): Outlook can carry out the scan.
    
- Non-zero value: Outlook should not scan Contacts folders on the store.
    

