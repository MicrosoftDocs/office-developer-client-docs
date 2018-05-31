---
title: "Launching a Form to Read a Message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 54a4b805-2ab7-4fb7-b0ea-4a33ead27451
description: "Last modified: July 23, 2011"
 
 
---

# Launching a Form to Read a Message

  
  
**Applies to**: Outlook 
  
Form server implementers should expect the following sequence of method calls to their form server and form objects when a client application loads a message:
  
1. The client application opens the form manager with a call to the [MAPIOpenFormMgr](mapiopenformmgr.md) function. 
    
2. The client application calls the [IMAPIFormMgr::LoadForm](imapiformmgr-loadform.md) method, which returns an object with [IMAPIForm](imapiformiunknown.md). The form manager may be released now if it will not be used for further form activations. Note that a call to **LoadForm** may take some time because the form manager may have to install the form server's executable files before proceeding. 
    
3. Optionally, the client application can prepare [IMAPIViewContext](imapiviewcontextiunknown.md) to control operations that may cause the form object to load the previous or next message in the folder. The client application can use the [IMAPIForm::SetViewContext](imapiform-setviewcontext.md) method to change the default view context that was set in the **LoadForm** call. 
    
4. The client application calls the [IPersistMessage::Load](ipersistmessage-load.md) method to load message data into the form object. 
    
5. The client application calls [IMAPIForm::DoVerb](imapiform-doverb.md) to invoke the open verb, passing the optional [IMAPIViewContext](imapiviewcontextiunknown.md) interface pointer. 
    
## See also



[Form Server Interactions](form-server-interactions.md)

