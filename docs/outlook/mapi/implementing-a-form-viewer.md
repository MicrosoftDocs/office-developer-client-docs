---
title: "Implementing a Form Viewer"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: a567185c-bd72-4307-928c-08cac5494c1a
description: "Last modified: July 23, 2011"
 
 
---

# Implementing a Form Viewer

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A form viewer includes three objects: a message site, a view advise sink, and a view context. Each of these objects allows you to interact with a form server and its forms.
  
A message site is an object that implements the [IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md) interface and assists form servers with tasks such as moving, saving, or deleting messages, creating new messages, or launching new form servers. Message sites are used by forms to get information about your client's status with respect to various service providers. For example, a form can use your message site to get a pointer to your current message store, a message, or a folder. 
  
There are two types of methods in the **IMAPIMessageSite** interface: 
  
- Methods that provide information to form objects.
    
- Methods that manipulate messages.
    
The methods that provide information to form objects are straightforward to implement. In all cases except [IMAPIMessageSite::GetSiteStatus](imapimessagesite-getsitestatus.md), you should already have available the information required by each method.
  
The methods that manipulate messages should act as if they had been triggered through your regular user interface. For example, if a form object calls your [IMAPIMessageSite::NewMessage](imapimessagesite-newmessage.md) method, behave as if the user had chosen to compose a new custom message with your regular user interface. Commands which typically generate this behavior are **Compose**, **Open**, **Reply**, **Reply to All Recipients**, and **Forward**. 
  
A view context is an object that implements the [IMAPIViewContext : IUnknown](imapiviewcontextiunknown.md) interface and provides form servers with a context for the current message, allowing servers to easily switch to the next or previous message in the folder. A form uses a view context for sharing information. With a view context object, a form can: 
  
- Register with your client for notifications.
    
- Activate the next or previous message in the folder.
    
- Get printing information.
    
- Get your client's status.
    
- Get a stream that can be used to save the text version of a message.
    
Similar to the methods in the [IMAPIMessageSite : IUnknown](imapimessagesiteiunknown.md) interface, the methods in **IMAPIViewContext** correlate with user actions and client features that relate to the view context. For example, a view context is involved with activating the next or previous message, sorting the contents of the folder, and filtering the contents of the folder. 
  
It is not important what mechanism you provide for users to activate these features, it is only important that the semantics of those features map well to the methods in the **IMAPIViewContext** interface. 
  
A view advise sink is an object that implements the [IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md) interface and handles notifications from form servers that affect your viewer and help forms and form viewers to work together. For more information, see [Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md). 
  

