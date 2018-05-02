---
title: "PidTagAttachEncoding Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachEncoding
api_type:
- HeaderDef
ms.assetid: 3b30cec6-da1e-4ef1-8c17-24b66f31cf0a
description: "Last modified: March 09, 2015"
---

# PidTagAttachEncoding Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains an ASN.1 object identifier that specifies the encoding for an attachment. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_ENCODING  <br/> |
|Identifier:  <br/> |0x3702  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

This property identifies the algorithm used to transform the data in an attachment.
  
 **Note** The **PR_ATTACH_ENCODING** and **PR_ATTACH_TAG** ( [PidTagAttachTag](pidtagattachtag-canonical-property.md)) properties should not be confused. They are not paired or related. **PR_ATTACH_TAG** identifies the application that originally generated the attachment. "Object" has a much more general meaning in the term object identifier, and in X.400, than in object-oriented programming. 
  
The object identifier syntax and sample object identifiers are defined in the MAPIOID.H header file. Values for **PR_ATTACH_ENCODING** are not limited to those defined in MAPIOID.H. For example, attached Macintosh files can use an identifier such as MacBinary. 
  
For complete information on these object identifiers, see the documentation on ASN.1, X.208, and X.209. The object identifier is found in the application-reference element of the FTBP (File Transfer Body Part) environment. 
  
## Related Resources

### Protocol Specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

