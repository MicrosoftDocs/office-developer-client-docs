---
title: "Launching a New Compose Form"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: ffceaa03-76f2-42e0-b28d-226f1f9cc889
description: "Last modified: July 23, 2011"
 
 
---

# Launching a New Compose Form

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Form server implementers should expect the following sequence of method calls to their form server and form objects when a client application opens a new message for composing:
  
1. The client application calls the [IMAPIFormMgr::ResolveMessageClass](imapiformmgr-resolvemessageclass.md) method to get class information about the form server's message class. 
    
2. The client application calls [IMAPIFormMgr::CreateForm](imapiformmgr-createform.md) to get a new form object. 
    
3. The MAPI form manager loads the form server, if it is not already in memory, and gets an [IMAPIForm](imapiformiunknown.md) interface from the form server. 
    
4. The client application takes the resulting **IMAPIForm** interface and calls the [IUnknown::QueryInterface](https://msdn.microsoft.com/library/54d5ff80-18db-43f2-b636-f93ac053146d%28Office.15%29.aspx) method to get the object's [IPersistMessage](ipersistmessageiunknown.md) interface. 
    
5. The client application calls the [IPersistMessage::InitNew](ipersistmessage-initnew.md) method to associate the form object with [IMessage](imessageimapiprop.md), view context, and advise sink objects.
    
6. The client application calls the [IMAPIForm::DoVerb](imapiform-doverb.md) method to invoke the open verb. 
    
## See also



[Form Server Interactions](form-server-interactions.md)

