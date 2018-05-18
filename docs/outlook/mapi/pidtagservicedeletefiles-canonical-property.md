---
title: "PidTagServiceDeleteFiles Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagServiceDeleteFiles
api_type:
- COM
ms.assetid: 9ec80a93-9e8f-46be-a1d4-7648aae47fec
description: "Last modified: March 09, 2015"
---

# PidTagServiceDeleteFiles Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a list of filenames that are to be deleted when the message service is uninstalled.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_DELETE_FILES, PR_SERVICE_DELETE_FILES_A, PR_SERVICE_DELETE_FILES_W  <br/> |
|Identifier:  <br/> |0x3D10  <br/> |
|Data type:  <br/> |PT_MV_STRING8, PT_MV_UNICODE  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

The filenames in the list contained in these properties are deleted from the computer when using the control panel to uninstall the message service. Do not include in the list any DLL that supports multiple message services, or additional message services could be inadvertently removed.
  
MAPI works only with filenames, and other strings passed to it, in the ANSI character set. Applications that use filenames in an OEM character set must convert them to ANSI before calling MAPI.
  
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

