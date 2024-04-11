---
title: "PidTagSearchFolderStorageType Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagSearchFolderStorageType
api_type:
- COM
ms.assetid: 1ec21942-47db-43a5-a6ee-ec6fd2135e8b
description: "Contains flags that specify the Binary Large Object (BLOB) data that appears in the PR_WB_SF_DEFINITION property."
---

# PidTagSearchFolderStorageType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains flags that specify the Binary Large Object (BLOB) data that appears in the **PR_WB_SF_DEFINITION** ([PidTagSearchFolderDefinition](pidtagsearchfolderdefinition-canonical-property.md)) property.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_WB_SF_STORAGE_TYPE  <br/> |
|Identifier:  <br/> |0x6846  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Search  <br/> |
   
## Remarks

The definitions of the flags are specified in [[MS-OXOSRCH]](https://msdn.microsoft.com/library/c72e49b8-78c7-4483-ad65-e46e9133673b%28Office.15%29.aspx). Search for **PR_WB_SF_STORAGE_TYPE**.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOSRCH]](https://msdn.microsoft.com/library/c72e49b8-78c7-4483-ad65-e46e9133673b%28Office.15%29.aspx)
  
> Specifies the properties and operations for manipulating a search folder list configuration.
    
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

