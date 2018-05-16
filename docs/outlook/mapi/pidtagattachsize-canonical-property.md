---
title: "PidTagAttachSize Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachSize
api_type:
- HeaderDef
ms.assetid: 768b3215-dd9f-4aa0-b52c-178ca81a7b07
description: "Last modified: March 09, 2015"
---

# PidTagAttachSize Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the sum, in bytes, of the sizes of all properties on an attachment. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_SIZE  <br/> |
|Identifier:  <br/> |0x0E20  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

It is recommended that attachment subobjects expose the **PR_ATTACH_SIZE** property. The sum contained in **PR_ATTACH_SIZE** includes the size of the **PR_ATTACH_DATA_BIN** ( [PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) or **PR_ATTACH_DATA_OBJ** ( [PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)) property. Accordingly, **PR_ATTACH_SIZE** is usually larger than the contents of the attachment alone. 
  
This property can be used to check the approximate size of the attachment before performing a remote transfer by modem and to display progress indicators when saving the attachment to disk. It is particularly useful with attached OLE objects. 
  
## Related Resources

### Protocol Specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Reference

[PidTagMessageSize Canonical Property](pidtagmessagesize-canonical-property.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

