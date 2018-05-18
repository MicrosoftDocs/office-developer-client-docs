---
title: "PidTagServiceEntryName Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagServiceEntryName
api_type:
- COM
ms.assetid: 783f08aa-fb5a-432d-b8bd-48d69f0e5c38
description: "Last modified: March 09, 2015"
---

# PidTagServiceEntryName Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the name of the entry point function for configuration of a message service.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_ENTRY_NAME  <br/> |
|Identifier:  <br/> |0x3D0B  <br/> |
|Data type:  <br/> |PT_STRING8  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

It is recommended that message service implementers provide a message service entry point, but the entry point is not required. However, the entry point should be supplied only if the related configuration properties exist. If these properties do not exist, MAPI assumes that no entry point is provided.
  
The dynamic-link library (DLL) in which the entry point function appears is named by the **PR_SERVICE_DLL_NAME** ([PidTagServiceDllName](pidtagservicedllname-canonical-property.md)) property.
  
For more information on message service entry points, see [Implementing a Service Provider Entry Point Function](implementing-a-service-provider-entry-point-function.md).
  
## Related Resources

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

