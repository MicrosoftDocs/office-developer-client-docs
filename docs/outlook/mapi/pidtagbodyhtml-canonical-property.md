---
title: "PidTagBodyHtml Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagBodyHtml
api_type:
- HeaderDef
ms.assetid: 93b9215a-5900-411c-a0ae-6bba62cd5a1e
description: "Contains the HTML version of the message text. These properties contain the same message text as the PR_BODY_CONTENT_LOCATION, but in HTML."
---

# PidTagBodyHtml Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the Hypertext Markup Language (HTML) version of the message text. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_BODY_HTML, PR_BODY_HTML_A, PR_BODY_HTML_W  <br/> |
|Identifier:  <br/> |0x1013  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

These properties contain the same message text as the **PR_BODY_CONTENT_LOCATION** ([PidTagBodyContentLocation](pidtagbodycontentlocation-canonical-property.md)), but in HTML. 
  
A message store that supports HTML indicates this by setting the **STORE_HTML_OK** flag in its **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)). 
  
 **Note** **STORE_HTML_OK** is not defined in versions of Mapidefs.h included with Microsoft® Exchange 2000 Server and earlier. If **STORE_HTML_OK** is undefined, use the value 0x00010000 instead. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
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

