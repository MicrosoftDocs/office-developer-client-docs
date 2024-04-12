---
title: "CONTAB_ENTRYID"
description: "CONTAB_ENTRYID contains the entry ID of the contacts folder. This article describes its members and remarks."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 84251222-dac4-4f4d-97b9-aa0e2cd26c44
---

# CONTAB_ENTRYID

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the entry ID of the contacts folder.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |msomapiutil.h  <br/> |
   
```cpp
#pragma pack(4) 
typedef struct _contab_entryid
{
    BYTE abFlags[4];
    MAPIUID muid;
    ULONG ulVersion;
    ULONG ulType;
    ULONG ulIndex;
    ULONG cbeid;
    BYTE abeid[1];
}   CONTAB_ENTRYID, *LPCONTAB_ENTRYID;
#pragma pack() 
```

## Members

 **abFlags**
  
> A bitmask of flags that provides information describing the object. For more information, see the description of the **abFlags** field of an [ENTRYID](entryid.md) structure. 
    
 **muid**
  
> GUID that identifies the store provider.
    
 **ulVersion**
  
> The version number of the **CONTAB_ENTRYID** structure. Must be set to CONTAB_VERSION. 
    
 **ulType**
  
> An integer representing the contact entry ID type. It must be one of the following values:
    
|**Name**|**Description**|
|:-----|:-----|
|CONTAB_USER  <br/> |A messaging user object. |
|CONTAB_DISTLIST  <br/> |A distribution list object. |
   
 **ulIndex**
  
> The index into the email property subset.
    
 **cbeid**
  
> The size of the entry identifier of the Contact message associated with this entry in the Contacts Address Book.
    
 **abeid**
  
> The entry identifier of the Contact message associated with this entry in the Contacts Address Book.
    
## Remarks

A Contacts Address Book is an Address Book that contains all the contact items in a Contacts folder that have either an email address or a fax number. Each entry in a Contacts Address Book is associated with either an email address or a fax number. Since a contact item can have up to three email addresses and three fax numbers, a contact item can be represented by up to six entries in the corresponding Contacts Address Book.
  
The purpose of a Contacts Address Book is to support users addressing email messages to contacts in a Contacts folder. The Contacts Address Book provider that Microsoft Outlook 2010 and Microsoft Outlook 2013 support is contab32.dll.
  
The **CONTAB_ENTRYID** structure supports a subset of the information that is present in the underlying MAPI Contact message. It identifies the Contact message that a particular Contacts Address Book entry is associated with. 
  
The **cbeid** and **abeid** fields are only valid when the **ulType** field value is set to CONTAB_DISTLIST or CONTAB_USER. When the **ulType** field value is set to CONTAB_ROOT, CONTAB_SUBROOT, or CONTAB_CONTAINER, the [DIR_ENTRYID](dir_entryid.md) structure should be used instead. 
  
## See also



[DIR_ENTRYID](dir_entryid.md)


[MAPI Structures](mapi-structures.md)

