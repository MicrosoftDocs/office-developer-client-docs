---
title: "PidTagReceiveFolderSettings Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagReceiveFolderSettings
api_type:
- COM
ms.assetid: 2f0b1679-05b0-4580-b6d2-474fe3f9d012
description: "Last modified: March 09, 2015"
---

# PidTagReceiveFolderSettings Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a table of a message store's receive folder settings.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RECEIVE_FOLDER_SETTINGS  <br/> |
|Identifier:  <br/> |0x3415  <br/> |
|Data type:  <br/> |PT_OBJECT  <br/> |
|Area:  <br/> |MAPI message store  <br/> |
   
## Remarks

This property can be excluded in [IMAPIProp::CopyTo](imapiprop-copyto.md) operations or included in [IMAPIProp::CopyProps](imapiprop-copyprops.md) operations. As a property of type PT_OBJECT, it cannot be successfully retrieved by the [IMAPIProp::GetProps](imapiprop-getprops.md) method; its contents should be accessed by the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method, requesting the interface with identifier IID_IMAPITable. Service providers must report it to the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method if it is set, but can optionally report it or not if it is not set. 
  
To retrieve table contents, a client application should call the [IMsgStore::GetReceiveFolderTable](imsgstore-getreceivefoldertable.md) method. For more information, see [Receive Folder Tables](receive-folder-tables.md).
  
This property contains a table of mappings of the receive folders for the message store. Calling **OpenProperty** on this property is equivalent to calling **GetReceiveFolderTable** on the message store. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

