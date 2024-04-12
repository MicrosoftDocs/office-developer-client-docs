---
title: "PidLidOfflineStatus Canonical Property"
description: Outlines the PidLidOfflineStatus canonical property, which determines the state of a document file on a server that implements [MS-LISTSWS].
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidOfflineStatus
api_type:
- COM
ms.assetid: ee69f0c4-b552-4cfd-8a39-a822d414549e
---

# PidLidOfflineStatus Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Determines the state of a document file on a server that implements [MS-LISTSWS].
  
|Property|Value|
|:-----|:-----|
|Associated properties  <br/> |dispidOfflineStatus  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x000085B9  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

The following table shows the possible values of this property.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Document is not checked out. |
|1  <br/> |Document is checked out to the current user. |
|2  <br/> |Document is not checked out, but the current user has a copy of the file saved for editing on the current computer. |
   
This property is calculated locally and is not sent to a server at any time unless a user drags the item to another account. In that case, it is treated as a user-defined custom property.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]] 
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

