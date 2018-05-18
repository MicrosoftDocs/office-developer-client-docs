---
title: "DIR_ENTRYID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 9e055269-f3bf-4b64-8384-3cbc372c0b34
description: "Last modified: March 09, 2015"
---

# DIR_ENTRYID

  
  
**Applies to**: Outlook 
  
Describes the properties of a directory entry id.
  
|||
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
|CONTAB_ROOT  <br/> |The root folder for a MAPI address book.  <br/> |
|CONTAB_SUBROOT  <br/> |A subfolder contained within the root folder of the MAPI address book object.  <br/> |
|CONTAB_CONTAINER  <br/> |An address book container object.  <br/> |
   
 **muidID**
  
> A GUID that identifies the logon object.
    
## Remarks

The structures **DIR_ENTRYID** and [CONTAB_ENTRYID](contab_entryid.md) are identical, except for the **ulType** member. The contents of the **ulType** member determine which structure is appropriate for the remaining fields. 
  
## See also

#### Reference

[CONTAB_ENTRYID](contab_entryid.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

