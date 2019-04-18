---
title: "PidTagProviderDllName Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagProviderDllName
api_type:
- COM
ms.assetid: 9ddb38eb-9a32-4dbe-b42c-6ea9db98acd2
description: "Last modified: March 09, 2015"
---

# PidTagProviderDllName Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the base file name of the MAPI service provider dynamic-link library (DLL).
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_PROVIDER_DLL_NAME, PR_PROVIDER_DLL_NAME_A, PR_PROVIDER_DLL_NAME_W  <br/> |
|Identifier:  <br/> |0x300A  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

MAPI uses a DLL file naming convention. MAPI appends the string 32 to the base DLL name to identify the version that runs on 32-bit platforms. For example, when the name MAPI.DLL is specified, MAPI constructs the name MAPI32.DLL to represent the corresponding 32-bit version of the DLL.
  
These properties should specify the base name. MAPI appends the string 32 as appropriate. Including the string 32 as part of this property results in an error.
  
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

