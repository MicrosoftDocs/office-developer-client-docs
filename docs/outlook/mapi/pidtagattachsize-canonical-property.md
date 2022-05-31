---
title: "PidTagAttachSize Canonical Property"
description: Outlines the PidTagAttachSize canonical property, which contains the sum, in bytes, of the sizes of all properties on an attachment. 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagAttachSize
api_type:
- HeaderDef
ms.assetid: 768b3215-dd9f-4aa0-b52c-178ca81a7b07
---

# PidTagAttachSize Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the sum, in bytes, of the sizes of all properties on an attachment. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_SIZE  <br/> |
|Identifier:  <br/> |0x0E20  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

It is recommended that attachment subobjects expose the **PR_ATTACH_SIZE** property. The sum contained in **PR_ATTACH_SIZE** includes the size of the **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) or **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)) property. Accordingly, **PR_ATTACH_SIZE** is usually larger than the contents of the attachment alone. 
  
This property can be used to check the approximate size of the attachment before performing a remote transfer by modem and to display progress indicators when saving the attachment to disk. It is particularly useful with attached OLE objects. 
  
## Related resources

### Protocol specifications

[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagMessageSize Canonical Property](pidtagmessagesize-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

