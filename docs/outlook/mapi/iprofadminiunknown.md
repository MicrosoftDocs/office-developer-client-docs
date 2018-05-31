---
title: "IProfAdmin  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProfAdmin
api_type:
- COM
ms.assetid: 274899cc-2894-4d99-84ec-f18121e856a0
description: "Last modified: March 09, 2015"
---

# IProfAdmin : IUnknown

  
  
**Applies to**: Outlook 
  
Supports the administration of profiles. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Exposed by:  <br/> |Profile administration object  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IProfAdmin  <br/> |
|Pointer type:  <br/> |LPPROFADMIN  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetLastError](iprofadmin-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error that occurred to a profile administration object.  <br/> |
|[GetProfileTable](iprofadmin-getprofiletable.md) <br/> |Provides access to the profile table, a table that contains information about all of the available profiles.  <br/> |
|[CreateProfile](iprofadmin-createprofile.md) <br/> |Creates a new profile.  <br/> |
|[DeleteProfile](iprofadmin-deleteprofile.md) <br/> |Deletes a profile.  <br/> |
|[ChangeProfilePassword](iprofadmin-changeprofilepassword.md) <br/> |Deprecated. Changes the password for a profile.  <br/> |
|[CopyProfile](iprofadmin-copyprofile.md) <br/> |Copies a profile.  <br/> |
|[RenameProfile](iprofadmin-renameprofile.md) <br/> |Assigns a new name to a profile.  <br/> |
|[SetDefaultProfile](iprofadmin-setdefaultprofile.md) <br/> |Sets or clears a client's default profile.  <br/> |
|[AdminServices](iprofadmin-adminservices.md) <br/> |Provides access to a message service administration object for making changes to the message services in a profile.  <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

