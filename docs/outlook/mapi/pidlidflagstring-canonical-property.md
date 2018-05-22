---
title: "PidLidFlagString Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidFlagString
api_type:
- COM
ms.assetid: 4cf1e08b-c869-4965-a1e4-512a0684700f
description: "Last modified: March 09, 2015"
---

# PidLidFlagString Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an index that identifies one of a set of pre-defined text strings associated with the flag.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidFlagStringEnum  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x000085C0  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Task  <br/> |
   
## Remarks

If this property is set, clients should use the corresponding string value in the tables below (for example, to substitute a string that is translated into the current user's language), and should ignore the value set in **dispidFlagRequest** ([PidLidFlagRequest](pidlidflagrequest-canonical-property.md)) and **dispidValidFlagStringProof** ([PidLidValidFlagStringProof](pidlidvalidflagstringproof-canonical-property.md)). 
  
Defaults suggested to the user for contact objects are as follows:
  
|**Value**|**English string**|
|:-----|:-----|
|0x00000000 or not present  <br/> | Follow the guidance related to displaying **dispidFlagRequest**.  <br/> |
|0x0000006E  <br/> |"Follow up"  <br/> |
|0x0000006F  <br/> |"Call"  <br/> |
|0x00000070  <br/> |"Arrange Meeting"  <br/> |
|0x00000071  <br/> |"Send Email"  <br/> |
|0x00000072  <br/> |"Send Letter"  <br/> |
   
Defaults suggested to the user for all other message objects are as follows:
  
|**Value**|**English string**|
|:-----|:-----|
|0x00000000 or not present  <br/> | Follow the guidance related to displaying **dispidFlagRequest**.  <br/> |
|0x00000001  <br/> |"Call"  <br/> |
|0x00000002  <br/> |"Do not Forward"  <br/> |
|0x00000003  <br/> |"Follow up"  <br/> |
|0x00000004  <br/> |"For Your Information"  <br/> |
|0x00000005  <br/> |"Forward"  <br/> |
|0x00000006  <br/> |"No Response Necessary"  <br/> |
|0x00000007  <br/> |"Read"  <br/> |
|0x00000008  <br/> |"Reply"  <br/> |
|0x00000009  <br/> |"Reply to All"  <br/> |
|0x0000000A  <br/> |"Review"  <br/> |
   
All strings specified above can be translated to the user's language, if appropriate.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOFLAG]](http://msdn.microsoft.com/library/f1e50be4-ed30-4c2a-b5cb-8ff3aaaf9b91%28Office.15%29.aspx)
  
> Specifies the properties and operations related to flagging.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

