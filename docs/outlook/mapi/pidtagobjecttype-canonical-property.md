---
title: "PidTagObjectType Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagObjectType
api_type:
- HeaderDef
ms.assetid: 37da4ff5-300d-479f-a8b4-6fc36df997d9
description: "Last modified: March 09, 2015"
---

# PidTagObjectType Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the type of an object. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_OBJECT_TYPE  <br/> |
|Identifier:  <br/> |0x0FFE  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Common  <br/> |
   
## Remarks

The object type contained in this property corresponds to the primary interface available for an object accessible through the **OpenEntry** interface. It is usually obtained by consulting the  _lpulObjType_ parameter returned by the appropriate **OpenEntry** method. When the interface is obtained in other ways, call [IMAPIProp::GetProps](imapiprop-getprops.md) to obtain the value for this property. 
  
This property can have exactly one of the following values:
  
MAPI_ABCONT 
  
> Address book container object 
    
MAPI_ADDRBOOK 
  
> Address book object 
    
MAPI_ATTACH 
  
> Message attachment object 
    
MAPI_DISTLIST 
  
> Distribution list object 
    
MAPI_FOLDER 
  
> Folder object 
    
MAPI_FORMINFO 
  
> Form object 
    
MAPI_MAILUSER 
  
> Messaging user object 
    
MAPI_MESSAGE 
  
> Message object 
    
MAPI_PROFSECT 
  
> Profile section object 
    
MAPI_SESSION 
  
> Session object 
    
MAPI_STATUS 
  
> Status object 
    
MAPI_STORE 
  
> Message store object
    
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
[[MS-NSPI]](https://msdn.microsoft.com/library/6dd0a3ea-b4d4-4a73-a857-add03a89a543%28Office.15%29.aspx)
  
> Handles a client's communications with a Name Service Provider Interface (NSPI) server.
    
[[MS-OXCFOLD]](https://msdn.microsoft.com/library/c0f31b95-c07f-486c-98d9-535ed9705fbf%28Office.15%29.aspx)
  
> Handles folder operations.
    
[[MS-OXCFXICS]](https://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles the order and flow for data transfers between a client and server.
    
[[MS-OXCMAIL]](https://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard email conventions to message objects.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXOAB]](https://msdn.microsoft.com/library/b4750386-66ec-4e69-abb6-208dd131c7de%28Office.15%29.aspx)
  
> Specifies the offline address book (OAB) file formats for the local address book objects cache.
    
[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for email message objects.
    
[[MS-OXOSRCH]](https://msdn.microsoft.com/library/c72e49b8-78c7-4483-ad65-e46e9133673b%28Office.15%29.aspx)
  
> Specifies the properties and operations for manipulating a search folder list configuration.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

