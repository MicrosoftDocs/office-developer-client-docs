---
title: "PidLidOfflineStatus Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidOfflineStatus
api_type:
- COM
ms.assetid: ee69f0c4-b552-4cfd-8a39-a822d414549e
description: "Last modified: March 09, 2015"
---

# PidLidOfflineStatus Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Determines the state of a document file on a server that implements [[MS-LISTSWS]](30b364cc-3837-4e83-9ce8-1963292e2ee5).
  
|||
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
|0  <br/> |Document is not checked out.  <br/> |
|1  <br/> |Document is checked out to the current user.  <br/> |
|2  <br/> |Document is not checked out, but the current user has a copy of the file saved for editing on the current computer.  <br/> |
   
This property is calculated locally and is not sent to a server at any time unless a user drags the item to another account. In that case, it is treated as a user-defined custom property.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]] 
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

