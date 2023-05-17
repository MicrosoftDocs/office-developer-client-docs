---
title: "IMSLogon  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMSLogon
api_type:
- COM
ms.assetid: d87093dc-f705-465f-ab3c-944ca0cd3e54
description: "Accesses resources in a message store logon object. The message store logon object is the part of an open message store provider that MAPI calls directly."
---

# IMSLogon : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Accesses resources in a message store logon object.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Message store logon objects  <br/> |
|Implemented by:  <br/> |Message store providers  <br/> |
|Called by:  <br/> |MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMSLogon  <br/> |
|Pointer type:  <br/> |LPMSLOGON  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[GetLastError](imslogon-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the last error that occurred for the message store object. |
|[Logoff](imslogon-logoff.md) <br/> |Logs off a message store provider. |
|[OpenEntry](imslogon-openentry.md) <br/> |Opens a folder or message object and returns a pointer to the object to provide further access. |
|[CompareEntryIDs](imslogon-compareentryids.md) <br/> |Compares two entry identifiers to determine whether they refer to the same object. |
|[Advise](imslogon-advise.md) <br/> |Registers an object with a message store provider for notifications about changes in the message store. |
|[Unadvise](imslogon-unadvise.md) <br/> |Removes an object's registration for notification of message store changes previously established by using a call to the **IMSLogon::Advise** method. |
|[OpenStatusEntry](imslogon-openstatusentry.md) <br/> |Opens a status object. |
   
## Remarks

The message store logon object is the part of an open message store provider that MAPI calls directly. There is a one-to-one correspondence between the message store logon object that MAPI calls and the message store object that client applications call; you can think of the logon and store objects as one object that exposes two interfaces. The two objects are created together and freed together.
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

