---
title: "IMAPISession  IUnknown"
description: "Describes the properties and vtable order of members for IMAPISessionIUnknown, which manages objects associated with a MAPI logon session."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession
api_type:
- COM
ms.assetid: 5650fa2a-6e62-451c-964e-363f7bee2344
---

# IMAPISession : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Manages objects associated with a MAPI logon session.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Exposed by:  <br/> |Session objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMAPISession  <br/> |
|Pointer type:  <br/> |LPMAPISESSION  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[GetLastError](imapisession-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous session error. |
|[GetMsgStoresTable](imapisession-getmsgstorestable.md) <br/> |Provides access to the message store table that contains information about all the message stores in the session profile. |
|[OpenMsgStore](imapisession-openmsgstore.md) <br/> |Opens a message store and returns an [IMsgStore](imsgstoreimapiprop.md) pointer for further access. |
|[OpenAddressBook](imapisession-openaddressbook.md) <br/> |Opens the MAPI integrated address book, returning an [IAddrBook](iaddrbookimapiprop.md) pointer for further access. |
|[OpenProfileSection](imapisession-openprofilesection.md) <br/> |Opens a section of the current profile and returns an [IProfSect](iprofsectimapiprop.md) pointer for further access. |
|[GetStatusTable](imapisession-getstatustable.md) <br/> |Provides access to the status table, a table that contains information about all the MAPI resources in the session. |
|[OpenEntry](imapisession-openentry.md) <br/> |Opens an object and returns an interface pointer for further access. |
|[CompareEntryIDs](imapisession-compareentryids.md) <br/> |Compares two entry identifiers to determine whether they refer to the same object. |
|[Advise](imapisession-advise.md) <br/> |Registers to receive notification of specified events that affect the session. |
|[Unadvise](imapisession-unadvise.md) <br/> |Cancels the sending of notifications previously set up with a call to the **Advise** method. |
|**MessageOptions** <br/> | *Not supported or documented.*  <br/> |
|**QueryDefaultMessageOpt** <br/> | *Not supported or documented.*  <br/> |
|[EnumAdrTypes](imapisession-enumadrtypes.md) <br/> |Deprecated. Returns the address types that can be handled by all of the transport providers in the session. |
|[QueryIdentity](imapisession-queryidentity.md) <br/> |Returns the entry identifier of the object that provides the primary identity for the session. |
|[Logoff](imapisession-logoff.md) <br/> |Ends a MAPI session. |
|[SetDefaultStore](imapisession-setdefaultstore.md) <br/> |Establishes a message store as the default message store for the session. |
|[AdminServices](imapisession-adminservices.md) <br/> |Returns an [IMsgServiceAdmin](imsgserviceadminiunknown.md) pointer for making changes to message services. |
|[ShowForm](imapisession-showform.md) <br/> |Displays a form. |
|[PrepareForm](imapisession-prepareform.md) <br/> |Creates a numeric token that the **ShowForm** method uses to access a message. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

