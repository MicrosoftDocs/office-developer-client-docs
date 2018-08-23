---
title: "PidNameAcceptLanguage Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidNameAcceptLanguage
api_type:
- COM
ms.assetid: 4b202bc1-f718-446a-950f-634ffee47baf
description: "Last modified: March 09, 2015"
---

# PidNameAcceptLanguage Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an [RFC3282] Accept-Language header field value.
  
|||
|:-----|:-----|
|Friendly names:  <br/> |AcceptLanguage  <br/> |
|Property set:  <br/> |PS_INTERNET_HEADERS  <br/> |
|Property name:  <br/> |Accept-Language  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Email  <br/> |
   
## Remarks

To set the value of this property, Multipurpose Internet Message Extensions (MIME) clients should write an Accept-Language header field with the desired value. MIME clients may write an X-Accept-Language header field instead. MIME readers should copy the value of either header field to the value of this property. If both header fields are present, MIME readers should use the Accept-Language header field.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard email conventions to message objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

