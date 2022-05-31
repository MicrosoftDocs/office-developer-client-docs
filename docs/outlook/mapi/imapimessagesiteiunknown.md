---
title: "IMAPIMessageSite  IUnknown"
description: "IMAPIMessageSiteIUnknown manipulates messages and is implemented by the form viewer code (typically a client application) that responds to such manipulation."
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
---

# IMAPIMessageSite : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Manipulates messages and is implemented by the form viewer code (typically a client application) that responds to such manipulation.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Message site objects  <br/> |
|Implemented by:  <br/> |Form viewers  <br/> |
|Called by:  <br/> |Form objects  <br/> |
|Interface identifier:  <br/> |IID_IMAPIMessageSite  <br/> |
|Pointer type:  <br/> |LPMAPIMESSAGESITE  <br/> |
   
## Vtable order

|Member | Description |
|:-----|:-----|
|[GetSession](imapimessagesite-getsession.md) <br/> |Returns the MAPI session in which the current message was created or opened. |
|[GetStore](imapimessagesite-getstore.md) <br/> |Returns the message store that contains the current message, if such a store exists. |
|[GetFolder](imapimessagesite-getfolder.md) <br/> |Returns the folder in which the current message was created or opened, if such a folder exists. |
|[GetMessage](imapimessagesite-getmessage.md) <br/> |Returns the current message. |
|[GetFormManager](imapimessagesite-getformmanager.md) <br/> |Returns a form manager interface, which a form server can use to open another form server. |
|[NewMessage](imapimessagesite-newmessage.md) <br/> |Creates a new message. |
|[CopyMessage](imapimessagesite-copymessage.md) <br/> |Copies the current message to a folder. |
|[MoveMessage](imapimessagesite-movemessage.md) <br/> |Moves the current message to a folder. |
|[DeleteMessage](imapimessagesite-deletemessage.md) <br/> |Deletes the current message. |
|[SaveMessage](imapimessagesite-savemessage.md) <br/> |Requests that the current message be saved. |
|[SubmitMessage](imapimessagesite-submitmessage.md) <br/> |Requests that the current message be queued for delivery. |
|[GetSiteStatus](imapimessagesite-getsitestatus.md) <br/> |Returns information from a message site object about the message site's capabilities for the current message. |
|[GetLastError](imapimessagesite-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous error occurring to the message site object. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

