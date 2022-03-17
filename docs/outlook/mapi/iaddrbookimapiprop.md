---
title: "IAddrBook  IMAPIProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook
api_type:
- COM
ms.assetid: 9ccacbc0-10d5-40f9-a12b-d090a21d0d49
description: "Last modified: March 09, 2015"
---

# IAddrBook : IMAPIProp

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Supports access to the MAPI address book and includes operations such as displaying common dialog boxes; opening containers, messaging users, and distribution lists; and performing name resolution.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Exposed by:  <br/> |Address book objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications, service providers  <br/> |
|Interface identifier:  <br/> |IID_IAddrBook  <br/> |
|Pointer type:  <br/> |LPADRBOOK  <br/> |
|Transaction model:  <br/> |Not writable  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[OpenEntry](iaddrbook-openentry.md) <br/> |Opens an address book entry and returns a pointer to an interface that can be used to access the entry. |
|[CompareEntryIDs](iaddrbook-compareentryids.md) <br/> |Compares two entry identifiers that belong to a particular address book provider to determine whether they refer to the same address book object. |
|[Advise](iaddrbook-advise.md) <br/> |Registers a client or service provider to receive notifications about changes to one or more entries in the address book. |
|[Unadvise](iaddrbook-unadvise.md) <br/> |Cancels a notification registration previously established for an address book entry. |
|[CreateOneOff](iaddrbook-createoneoff.md) <br/> |Creates an entry identifier for a one-off address. |
|[NewEntry](iaddrbook-newentry.md) <br/> |Adds a new recipient to an address book container or to the recipient list of an outgoing message. |
|[ResolveName](iaddrbook-resolvename.md) <br/> |Performs name resolution, assigning entry identifiers to recipients in a recipient list. |
|[Address](iaddrbook-address.md) <br/> |Displays the Outlook address book dialog box. |
|[Details](iaddrbook-details.md) <br/> |Displays a dialog box that shows details about a particular address book entry. |
|**RecipOptions** <br/> | *Not supported or documented.*  <br/> |
|**QueryDefaultRecipOpt** <br/> | *Not supported or documented.*  <br/> |
|[GetPAB](iaddrbook-getpab.md) <br/> |Returns the entry identifier of the container that is designated as the personal address book (PAB). |
|[SetPAB](iaddrbook-setpab.md) <br/> |Designates a particular container as the personal address book (PAB). |
|[GetDefaultDir](iaddrbook-getdefaultdir.md) <br/> |Returns the entry identifier for the initial address book container. |
|[SetDefaultDir](iaddrbook-setdefaultdir.md) <br/> |Establishes the specified container as the default address book container that is initially made available. |
|[GetSearchPath](iaddrbook-getsearchpath.md) <br/> |Returns an ordered list of entry identifiers of the containers to be included in the name resolution process initiated by the [ResolveName](iaddrbook-resolvename.md) method. |
|[SetSearchPath](iaddrbook-setsearchpath.md) <br/> |Sets a new search path in the profile that is used for the name resolution process. |
|[PrepareRecips](iaddrbook-preparerecips.md) <br/> |Prepares a recipient list for later use by the messaging system. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

