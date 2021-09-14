---
title: "IMAPIMessageSite  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIMessageSite
api_type:
- COM
ms.assetid: 883448f5-0d3f-486d-80a3-7b961c209cd0
description: "Last modified: March 09, 2015"
---

# IMAPIMessageSite : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Manipulates messages and is implemented by the form viewer code (typically a client application) that responds to such manipulation.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Message site objects  <br/> |
|Implemented by:  <br/> |Form viewers  <br/> |
|Called by:  <br/> |Form objects  <br/> |
|Interface identifier:  <br/> |IID_IMAPIMessageSite  <br/> |
|Pointer type:  <br/> |LPMAPIMESSAGESITE  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetSession](imapimessagesite-getsession.md) <br/> |Returns the MAPI session in which the current message was created or opened.  <br/> |
|[GetStore](imapimessagesite-getstore.md) <br/> |Returns the message store that contains the current message, if such a store exists.  <br/> |
|[GetFolder](imapimessagesite-getfolder.md) <br/> |Returns the folder in which the current message was created or opened, if such a folder exists.  <br/> |
|[GetMessage](imapimessagesite-getmessage.md) <br/> |Returns the current message.  <br/> |
|[GetFormManager](imapimessagesite-getformmanager.md) <br/> |Returns a form manager interface, which a form server can use to open another form server.  <br/> |
|[NewMessage](imapimessagesite-newmessage.md) <br/> |Creates a new message.  <br/> |
|[CopyMessage](imapimessagesite-copymessage.md) <br/> |Copies the current message to a folder.  <br/> |
|[MoveMessage](imapimessagesite-movemessage.md) <br/> |Moves the current message to a folder.  <br/> |
|[DeleteMessage](imapimessagesite-deletemessage.md) <br/> |Deletes the current message.  <br/> |
|[SaveMessage](imapimessagesite-savemessage.md) <br/> |Requests that the current message be saved.  <br/> |
|[SubmitMessage](imapimessagesite-submitmessage.md) <br/> |Requests that the current message be queued for delivery.  <br/> |
|[GetSiteStatus](imapimessagesite-getsitestatus.md) <br/> |Returns information from a message site object about the message site's capabilities for the current message.  <br/> |
|[GetLastError](imapimessagesite-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring to the message site object.  <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

