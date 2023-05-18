---
title: "DIR_ENTRYID"
description: "DIR_ENTRYID describes the properties of a directory entry id. This article describes its members and remarks."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 9e055269-f3bf-4b64-8384-3cbc372c0b34
---

# DIR_ENTRYID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes the properties of a directory entry id.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |entryid.h  <br/> |
   
```cpp
#pragma pack(4)
typedef struct _dir_entryid
{
    BYTE abFlags[4]; 
    MAPIUID muid; 
    ULONG ulVersion; 
    ULONG ulType; 
    MAPIUID muidID; 
}   DIR_ENTRYID, *LPDIR_ENTRYID; 
#pragma pack()
```

## Members

 **abFlags**
  
> A bitmask of flags that provides information describing the object. For more information, see the description of the **abFlags** field of an [ENTRYID](entryid.md) structure. 
    
 **muid**
  
> GUID that identifies the store provider.
    
 **ulVersion**
  
> The version number of the **DIR_ENTRYID** structure. Must be set to CONTAB_VERSION. 
    
 **ulType**
  
> An integer representing the directory entry ID type. It must be one of the following values:
    
|**Name**|**Description**|
|:-----|:-----|
|CONTAB_ROOT  <br/> |The root folder for a MAPI address book. |
|CONTAB_SUBROOT  <br/> |A subfolder contained within the root folder of the MAPI address book object. |
|CONTAB_CONTAINER  <br/> |An address book container object. |
   
 **muidID**
  
> A GUID that identifies the logon object.
    
## Remarks

The **DIR_ENTRYID** structure is a prefix of [CONTAB_ENTRYID](contab_entryid.md). The contents of the **ulType** member determine which structure is appropriate for the remaining fields. 
  
## See also



[CONTAB_ENTRYID](contab_entryid.md)


[MAPI Structures](mapi-structures.md)

