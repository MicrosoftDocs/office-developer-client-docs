---
title: "PidTagServiceDllName Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagServiceDllName
api_type:
- COM
ms.assetid: a651af84-1711-449e-ba7e-5ce09cafa02b
description: "Last modified: March 09, 2015"
---

# PidTagServiceDllName Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the filename of the DLL containing the message service provider entry point function to call for configuration.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_DLL_NAME, PR_SERVICE_DLL_NAME_A, PR_SERVICE_DLL_NAME_W  <br/> |
|Identifier:  <br/> |0x3D0A  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

When the entry point function name appears in the **PR_SERVICE_ENTRY_NAME** ([PidTagServiceEntryName](pidtagserviceentryname-canonical-property.md)) method, it indicates that the entry point exists.
  
MAPI uses a DLL file naming convention. The base filename contains up to six characters that uniquely identify the DLL. MAPI appends the string 32 to the base DLL name to identify the version that runs on 32-bit platforms. For example, when the name MAPI.DLL is specified, MAPI constructs the name MAPI32.DLL to represent the corresponding 32-bit version of the DLL.
  
These properties should specify the base name. MAPI appends the string 32 as appropriate. Including the string 32 as part of these properties result in an error.
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Reference

[PidTagProviderDllName Canonical Property](pidtagproviderdllname-canonical-property.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

