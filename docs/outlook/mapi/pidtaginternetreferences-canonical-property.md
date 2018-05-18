---
title: "PidTagInternetReferences Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagInternetReferences
api_type:
- HeaderDef
ms.assetid: 645fe61d-414a-455e-b034-db3cfd003b9d
description: "Last modified: March 09, 2015"
---

# PidTagInternetReferences Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the value of a Multipurpose Internet Mail Extensions (MIME) message's References header field.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_INTERNET_REFERENCES, PR_INTERNET_REFERENCES_A, PR_INTERNET_REFERENCES_W  <br/> |
|Identifier:  <br/> |0x1039  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MIME  <br/> |
   
## Remarks

To generate a References header field, clients must set these properties to the desired value. MIME writers must copy the value of these properties to the References header field.
  
To set the value of these properties, MIME clients must write the desired value to a References header field. MIME readers must copy the value of the References header field to these properties. MIME readers may truncate the value of these properties if it exceeds 64KB in length.
  
## Related resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard e-mail conventions to message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

