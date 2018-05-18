---
title: "PidTagAttachMethod Canonical Property"
 
 
manager: soliver
ms.date: 9/7/2016
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachMethod
api_type:
- HeaderDef
ms.assetid: 32089213-ef7b-4152-84ab-b44e9911332b
description: "Last modified: September 07, 2016"
---

# PidTagAttachMethod Canonical Property

 
  
**Applies to**: Outlook 
  
Contains a MAPI-defined constant representing the way the contents of an attachment can be accessed. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_METHOD  <br/> |
|Identifier:  <br/> |0x3705  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

This property can have exactly one of the following values:
  
NO_ATTACHMENT 
  
> The attachment has just been created. 
    
ATTACH_BY_VALUE 
  
> The **PR_ATTACH_DATA_BIN** ([PidTagAttachDataBinary](pidtagattachdatabinary-canonical-property.md)) property contains the attachment data. 
    
ATTACH_BY_REFERENCE 
  
> The **PR_ATTACH_PATHNAME** ([PidTagAttachPathname](pidtagattachpathname-canonical-property.md)) or **PR_ATTACH_LONG_PATHNAME** ([PidTagAttachLongPathname](pidtagattachlongpathname-canonical-property.md)) property contains a fully-qualified path identifying the attachment to recipients with access to a common file server. 
    
ATTACH_BY_REF_RESOLVE 
  
> The **PR_ATTACH_PATHNAME** or **PR_ATTACH_LONG_PATHNAME** property contains a fully-qualified path identifying the attachment. 
    
ATTACH_BY_REF_ONLY 
  
> The **PR_ATTACH_PATHNAME** or **PR_ATTACH_LONG_PATHNAME** property contains a fully-qualified path identifying the attachment. 
    
ATTACH_EMBEDDED_MSG 
  
> The **PR_ATTACH_DATA_OBJ** ([PidTagAttachDataObject](pidtagattachdataobject-canonical-property.md)) property contains an embedded object that supports the **IMessage** interface. 
    
ATTACH_OLE 
  
> The attachment is an embedded OLE object.
    
ATTACH_BY_WEBREFERENCE 
  
> The attachment content is not in the message. 
    
When created, all attachment objects have an initial **PR_ATTACH_METHOD** value of **NO_ATTACHMENT**. 
  
Client applications and service providers are only required to support the attachment method represented by the **ATTACH_BY_VALUE** value. The other attachment methods are optional. The message store does not enforce any consistency between the value of **PR_ATTACH_METHOD** and the values of the other attachment properties. 
  
Universal naming convention (UNC) names are recommended for fully-qualified paths, which should be used with **ATTACH_BY_REFERENCE** and **ATTACH_BY_REF_ONLY**. With **ATTACH_BY_REF_RESOLVE**, an absolute path is faster, because the MAPI spooler converts the attachment to **ATTACH_BY_VALUE**. 
  
If **ATTACH_BY_REFERENCE** is set, **PR_ATTACH_DATA_BIN** must be empty. An outbound gateway can turn an **ATTACH_BY_REFERENCE** attachment into an **ATTACH_BY_VALUE** attachment by copying the attachment data into the **PR_ATTACH_DATA_BIN** property. 
  
If **ATTACH_BY_REF_RESOLVE** is set, **PR_ATTACH_DATA_BIN** must be empty. When the message that contains the **ATTACH_BY_REF_RESOLVE** attachment is sent, the MAPI spooler copies the attachment data into an **ATTACH_BY_VALUE** attachment. This resolution process places the attachment data in **PR_ATTACH_DATA_BIN**. 
  
If **ATTACH_BY_REF_ONLY** is set, **PR_ATTACH_DATA_BIN** must be empty, and the messaging system never resolves the attachment reference. Use this value when you want to send the link but not the data. 
  
When the OLE object is in OLE 2.0 **IStorage** format, the data is accessible through **PR_ATTACH_DATA_OBJ**. When the OLE object is in OLE 1.0 **OLESTREAM** format, the data is accessible through **PR_ATTACH_DATA_BIN** as an **IStream**. The type of the OLE encoding can be determined by the **PR_ATTACH_TAG** ([PidTagAttachTag](pidtagattachtag-canonical-property.md)) value. 
  
For more information on OLE interfaces and formats, see the  *OLE Programmer's Reference*  . 
  
## Remarks

When the **PR_ATTACH_METHOD** is **ATTACH_BY_WEBREFERENCE**, the attachment content is not in the message. Instead, the **PR_ATTACH_LONG_FILENAME** property contains an absolute URL to the attachment content, which is stored online. 
  
## Related resources

### Protocol Specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagStoreSupportMask Canonical Property](pidtagstoresupportmask-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

