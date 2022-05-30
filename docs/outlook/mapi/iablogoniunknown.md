---
title: "IABLogon  IUnknown"
description: Describes IABLogon and provides methods and properties.
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IABLogon
api_type:
- COM
ms.assetid: fe340182-f41e-42e7-b8e8-cc005b1e9a5f
---

# IABLogon : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Accesses resources in an address book provider.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Address book logon objects  <br/> |
|Implemented by:  <br/> |Address book providers  <br/> |
|Called by:  <br/> |MAPI  <br/> |
|Interface identifier:  <br/> |IID_IABLogon  <br/> |
|Pointer type:  <br/> |LPABLOGON  <br/> |
   
## Vtable order

|Member | Description |
|:-----|:-----|
|[GetLastError](iablogon-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous address book provider error. |
|[Logoff](iablogon-logoff.md) <br/> |Initiates the logoff process. |
|[OpenEntry](iablogon-openentry.md) <br/> |Opens a container, messaging user, or distribution list, and returns a pointer to an interface implementation to provide further access. |
|[CompareEntryIDs](iablogon-compareentryids.md) <br/> |Compares two entry identifiers to determine whether they refer to the same object. |
|[Advise](iablogon-advise.md) <br/> |Registers the caller to receive notification of specified events that affect a container, messaging user, or distribution list. |
|[Unadvise](iablogon-unadvise.md) <br/> |Cancels notifications that were previously set up with a call to the **Advise** method. |
|[OpenStatusEntry](iablogon-openstatusentry.md) <br/> |Opens the provider's status object. |
|[OpenTemplateID](iablogon-opentemplateid.md) <br/> |Opens a recipient entry that has data residing in a host address book provider. |
|[GetOneOffTable](iablogon-getoneofftable.md) <br/> |Returns a table of one-off templates for creating recipients to be added to the recipient list of an outgoing message. |
|[PrepareRecips](iablogon-preparerecips.md) <br/> |Prepares a recipient list for later use by the messaging system. |
   
## Remarks

For general information about the methods of the **IABLogon** interface, see [Implementing Service Provider Logon](implementing-service-provider-logon.md).
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

