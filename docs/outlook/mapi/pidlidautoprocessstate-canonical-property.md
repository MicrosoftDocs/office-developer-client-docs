---
title: "PidLidAutoProcessState Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidAutoProcessState
api_type:
- COM
ms.assetid: 9e724af6-5b56-4eb3-a94c-1015ebce197c
description: "Last modified: March 09, 2015"
---

# PidLidAutoProcessState Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies the options that are used in automatic processing of e-mail messages.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSniffState  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x0000851A  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

The property may be absent, in which case the default value of "0x00000000" is used. If set, this property must be set to one of the values in the following table.
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |Do not automatically process the message.  <br/> |
|0x00000001  <br/> |Process the message automatically or when the message is opened.  <br/> |
|0x00000002  <br/> |Process the message only when the message is opened.  <br/> |
   
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for e-mail message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

