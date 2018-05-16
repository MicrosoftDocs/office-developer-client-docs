---
title: "PidTagEmsAbServer Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagEmsAbServer
api_type:
- HeaderDef
ms.assetid: de942619-2507-8fe0-bc81-f9da9ef7266f
description: "Last modified: March 09, 2015"
---

# PidTagEmsAbServer Canonical Property

  
  
**Applies to**: Outlook 
  
Specifies either the path of an address book container in an offline scenario or the fully qualified domain name of the global catalog server where the address book container resides in an online scenario.
  
## 

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_EMS_AB_SERVER, PR_EMS_AB_SERVER_A, PR_EMS_AB_SERVER_W  <br/> |
|Identifier:  <br/> |0xFFFE  <br/> |
|Data type:  <br/> |PT_TSTRING  <br/> |
|Area:  <br/> |Address Book  <br/> |
   
## Remarks

This property has the property type reset to **PT_UNICODE** when it is compiled with the  `UNICODE` symbol on a Unicode platform, and to **PT_STRING8** when it is not compiled with the  `UNICODE` symbol. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions.
    
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

