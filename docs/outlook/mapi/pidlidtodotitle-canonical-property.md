---
title: "PidLidToDoTitle Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidToDoTitle
api_type:
- COM
ms.assetid: 94cf031f-4c78-441d-9c01-55905b4974e0
description: "Last modified: March 09, 2015"
---

# PidLidToDoTitle Canonical Property

  
  
**Applies to**: Outlook 
  
Contains user-specifiable text to identify this message object in a consolidated to-do list.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidToDoTitle  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x000085A4  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

This property must not be set on a task. To indicate an empty property, do not set this property to the zero-length string, but instead delete it. 
  
When flagging a message object, and the property does not exist, a client should write the value of **PR_NORMALIZED_SUBJECT** ( [PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md)) to this property.
  
In a consolidated to-do list, if this property does not exist, a client should substitute the value of the **PR_NORMALIZED_SUBJECT** property when displaying this property in the to-do list. 
  
On a draft message object, if the client implements sender flags, this property should be set to the same value as **dispidRequest** ( [PidLidFlagRequest](pidlidflagrequest-canonical-property.md)).
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications
    
[[MS-OXOFLAG]](http://msdn.microsoft.com/library/f1e50be4-ed30-4c2a-b5cb-8ff3aaaf9b91%28Office.15%29.aspx)
  
> Specifies the properties and operations related to flagging.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Reference

[PidTagNormalizedSubject Canonical Property](pidtagnormalizedsubject-canonical-property.md)
  
[PidLidFlagRequest Canonical Property](pidlidflagrequest-canonical-property.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

