---
title: "IProfAdmin  IUnknown"
description: "Describes the properties and vtable order of members for IProfAdmin IUnknown, which supports the administration of profiles."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IProfAdmin
api_type:
- COM
ms.assetid: 274899cc-2894-4d99-84ec-f18121e856a0
---

# IProfAdmin : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Supports the administration of profiles. 
  
|Property|Value|
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Exposed by:  <br/> |Profile administration object  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IProfAdmin  <br/> |
|Pointer type:  <br/> |LPPROFADMIN  <br/> |
   
## Vtable order

|Member|Description|
|:-----|:-----|
|[GetLastError](iprofadmin-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error that occurred to a profile administration object. |
|[GetProfileTable](iprofadmin-getprofiletable.md) <br/> |Provides access to the profile table, a table that contains information about all of the available profiles. |
|[CreateProfile](iprofadmin-createprofile.md) <br/> |Creates a new profile. |
|[DeleteProfile](iprofadmin-deleteprofile.md) <br/> |Deletes a profile. |
|[ChangeProfilePassword](iprofadmin-changeprofilepassword.md) <br/> |Deprecated. Changes the password for a profile. |
|[CopyProfile](iprofadmin-copyprofile.md) <br/> |Copies a profile. |
|[RenameProfile](iprofadmin-renameprofile.md) <br/> |Assigns a new name to a profile. |
|[SetDefaultProfile](iprofadmin-setdefaultprofile.md) <br/> |Sets or clears a client's default profile. |
|[AdminServices](iprofadmin-adminservices.md) <br/> |Provides access to a message service administration object for making changes to the message services in a profile. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

