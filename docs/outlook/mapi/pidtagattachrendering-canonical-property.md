---
title: "PidTagAttachRendering Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachRendering
api_type:
- HeaderDef
ms.assetid: 1f31f7f4-fbda-4337-95e5-5474dd1bf84a
description: "Last modified: March 09, 2015"
---

# PidTagAttachRendering Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a Microsoft Windows metafile with rendering information for an attachment. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_RENDERING  <br/> |
|Identifier:  <br/> |0x3709  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

The purpose of this property is to provide an icon or other pictorial representation that can be displayed within the parent message at the point of attachment. Such representation typically includes the name of the attachment, if any, and the nature of the attachment, such as a Microsoft Office Word document. A client application can use this representation in the display of the message. 
  
For an attached file, this property usually portrays an icon for the file. 
  
For an attached message, this property is typically not set. A client application needing to render an attached message should obtain its **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property, call [IMAPIFormMgr::ResolveMessageClass](imapiformmgr-resolvemessageclass.md) for a pointer to the corresponding form information object, open the [IMAPIFormInfo](imapiforminfoimapiprop.md) interface on that object, and use **GetProps** to retrieve the **PR_ICON** ([PidTagIcon](pidtagicon-canonical-property.md)) or **PR_MINI_ICON** ([PidTagMiniIcon](pidtagminiicon-canonical-property.md)) property. 
  
For an embedded static OLE object, this property contains a Microsoft Windows metafile that can be used to draw the attachment representation in a window. 
  
For an embedded dynamic OLE object, the client should use the OLE data to generate the rendering information. 
  
In all cases, the client application should be aware that this property is usually several hundred bytes in size and is subject to truncation in the attachment table. If a client wishes to render the attachment from this property without opening the attachment itself, it must work within the table truncation rule. For more information, see [Working with Large Columns](working-with-large-columns.md). 
  
## Related resources

### Protocol specifications

[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

