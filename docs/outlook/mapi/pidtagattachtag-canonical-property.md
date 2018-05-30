---
title: "PidTagAttachTag Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachTag
api_type:
- HeaderDef
ms.assetid: 3d223809-b697-47c6-bc3c-2206aff7ad33
description: "Last modified: March 09, 2015"
---

# PidTagAttachTag Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an ASN.1 object identifier specifying the application that supplied an attachment. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_TAG  <br/> |
|Identifier:  <br/> |0x370A  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

This property identifies the application that originally generated the attachment.
  
 **Note** The **PR_ATTACH_ENCODING** ([PidTagAttachEncoding](pidtagattachencoding-canonical-property.md)) and **PR_ATTACH_TAG** properties should not be confused. They are not paired or related. **PR_ATTACH_ENCODING** identifies the algorithm used to transform the data in an attachment. "Object" has a much more general meaning in the term object identifier, and in X.400 usage, than in object-oriented programming. 
  
The object identifier syntax and sample object identifiers are defined in the MAPIOID.H header file. Values for **PR_ATTACH_TAG** are not limited to those defined in MAPIOID.H. 
  
For complete information on these object identifiers, see the documentation on ASN.1, X.208, and X.209. The object identifier is found in the application-reference element of the File Transfer Body Part (FTBP) environment. 
  
## Related resources

### Protocol specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagAttachMimeTag Canonical Property](pidtagattachmimetag-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

