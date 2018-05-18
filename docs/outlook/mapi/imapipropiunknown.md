---
title: "IMAPIProp  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProp
api_type:
- COM
ms.assetid: 3c9e4e05-cd3a-4b56-9dff-879e33ff6fd5
description: "Last modified: March 09, 2015"
---

# IMAPIProp : IUnknown

  
  
**Applies to**: Outlook 
  
Enables clients, service providers, and MAPI to work with properties. All objects that support properties implement this interface.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |No object exposes this interface directly.  <br/> |
|Implemented by:  <br/> |Service providers and MAPI  <br/> |
|Called by:  <br/> |Client applications, service providers, and MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMAPIProp  <br/> |
|Pointer type:  <br/> |LPMAPIPROP  <br/> |
|Transaction model:  <br/> |Abstract class, never implemented  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetLastError](imapiprop-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error.  <br/> |
|[SaveChanges](imapiprop-savechanges.md) <br/> |Makes permanent any changes that were made to an object since the last save operation.  <br/> |
|[GetProps](imapiprop-getprops.md) <br/> |Retrieves the property value of one or more properties of an object.  <br/> |
|[GetPropList](imapiprop-getproplist.md) <br/> |Returns property tags for all properties.  <br/> |
|[OpenProperty](imapiprop-openproperty.md) <br/> |Returns a pointer to an interface that can be used to access a property.  <br/> |
|[SetProps](imapiprop-setprops.md) <br/> |Updates one or more properties.  <br/> |
|[DeleteProps](imapiprop-deleteprops.md) <br/> |Deletes one or more properties from an object.  <br/> |
|[CopyTo](imapiprop-copyto.md) <br/> |Copies or moves all properties, except for specifically excluded properties.  <br/> |
|[CopyProps](imapiprop-copyprops.md) <br/> |Copies or moves selected properties.  <br/> |
|[GetNamesFromIDs](imapiprop-getnamesfromids.md) <br/> |Provides the property names that correspond to one or more property identifiers.  <br/> |
|[GetIDsFromNames](imapiprop-getidsfromnames.md) <br/> |Provides the property identifiers that correspond to one or more property names.  <br/> |
   
## Remarks

 **IMAPIProp** is the base interface for the following interfaces: 
  
- [IAttach](iattachimapiprop.md)
    
- [IMailUser](imailuserimapiprop.md)
    
- [IMAPIContainer](imapicontainerimapiprop.md)
    
- [IMAPIFormInfo](imapiforminfoimapiprop.md)
    
- [IMAPIStatus](imapistatusimapiprop.md)
    
- [IMessage](imessageimapiprop.md)
    
- [IMsgStore](imsgstoreimapiprop.md)
    
- [IProfSect](iprofsectimapiprop.md)
    
- [IPropData](ipropdataimapiprop.md)
    
## See also



[MAPI Interfaces](mapi-interfaces.md)

