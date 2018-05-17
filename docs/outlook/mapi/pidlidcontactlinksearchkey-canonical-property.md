---
title: "PidLidContactLinkSearchKey Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidContactLinkSearchKey
api_type:
- COM
ms.assetid: 82d21d38-a6c6-4e12-85b1-8158b2f5cce7
description: "Last modified: March 09, 2015"
---

# PidLidContactLinkSearchKey Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the list of **SearchKeys** for the contact linked to by this message object. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidContactLinkSearchKey  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008584  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

|**Length in bytes**|**Description**|**Notes**|
|:-----|:-----|:-----|
|2  <br/> |ContactEntryCount  <br/> |None  <br/> |
|variable  <br/> |SearchKey data  <br/> |Repeats ContactEntryCount times  <br/> |
   
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

