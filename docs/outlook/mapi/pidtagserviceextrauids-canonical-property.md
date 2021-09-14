---
title: "PidTagServiceExtraUids Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagServiceExtraUids
api_type:
- COM
ms.assetid: 4838a9af-7818-49aa-ace8-cb94dda8471f
description: "Last modified: March 09, 2015"
---

# PidTagServiceExtraUids Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a list of [MAPIUID](mapiuid.md) structures that identify additional profile sections for the message service. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_EXTRA_UIDS  <br/> |
|Identifier:  <br/> |0x3D0D  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

New profile sections can be created for each message filter. When the information about the message service is to be copied to another profile, it is important to copy the additional profile sections for the filters as well. A service provider that uses additional profile sections can store the **MAPIUID** structures of those profile sections in **PR_SERVICE_EXTRA_UIDS**, which allows MAPI to copy the additional message service information.
  
## Related resources

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

