---
title: "PidTagServiceSupportFiles Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagServiceSupportFiles
api_type:
- COM
ms.assetid: df4be986-62a8-49d6-8eca-25b55c74f830
description: "Last modified: March 09, 2015"
---

# PidTagServiceSupportFiles Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains a list of the files that belong to the message service.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SERVICE_SUPPORT_FILES, PR_SERVICE_SUPPORT_FILES_A, PR_SERVICE_SUPPORT_FILES_W  <br/> |
|Identifier:  <br/> |0x3D0F  <br/> |
|Data type:  <br/> |PT_MV_STRING8, PT_MV_UNICODE  <br/> |
|Area:  <br/> |MAPI profile  <br/> |
   
## Remarks

Using a dialog box in the control panel applet, a user can obtain the list of files that belong to the message service. For example, the user can obtain the names of all dynamic-link libraries (DLLs) that belong to the service. The user can then seek additional details about the specified files, such as the names and version numbers of all the DLLs. MAPI uses the these properties to create a support file list in a dialog box for messaging user selection.
  
MAPI works only with filenames, and other strings passed to it, in the Active Directory Service Interfaces (ANSI) character set. Client applications that use filenames in an original equipment manufacturer (OEM) character set must convert them to ANSI before calling MAPI.
  
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

