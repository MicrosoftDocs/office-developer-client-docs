---
title: "Sending and Receiving Form Notifications"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: a4374728-e2bc-47d9-8b03-ba09545a38d8
description: "Last modified: July 23, 2011"
 
 
---

# Sending and Receiving Form Notifications

  
  
**Applies to**: Outlook 
  
Form notifications are used in MAPI to facilitate communication both from the form to your viewer as well as from your viewer to the form.
  
Forms send notifications to your viewer when one of the following events occur:
  
- The form is closed.
    
- A new message is loaded in the form.
    
- A save operation is completed.
    
- A message is sent.
    
Each of these event types correspond to a particular method in [IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md), one of the interfaces that your form viewer must implement. When an event occurs, the form calls the corresponding **IMAPIViewAdviseSink** method in your viewer's advise sink. For example, when a new message arrives that your viewer should include in its display, the form calls your [IMAPIViewAdviseSink::OnNewMessage](imapiviewadvisesink-onnewmessage.md) method. 
  
Implement your view advise sink in a way that makes sense for your viewer; there is no standard implementation. For example, in **OnNewMessage** you can update the view of the current folder's contents table to include the newly arrived message. In [IMAPIViewAdviseSink::OnSubmitted](imapiviewadvisesink-onsubmitted.md), the method that is called when you receive a submitted message event, you can copy the submitted message to a Sent Items folder.
  
Forms receive notification from your viewer when a change occurs that affects the form and when you are loading a new message. To notify a form, call one of the methods of **IMAPIFormAdviseSink**: [IMAPIFormAdviseSink::OnChange](imapiformadvisesink-onchange.md) or [IMAPIFormAdviseSink::OnActivateNext](imapiformadvisesink-onactivatenext.md). Call **OnChange** to communicate status. For example, if the form is displaying the last item in a folder when a new message arrives, call **OnChange** with the VCSTATUS_NEXT flag set to tell the form that there is now a next item. 
  
Call **OnActivateNext** to alert the form to the arrival of a new message that it may or may not be able to display. Pass the message class of the message to **OnActivateNext**. 
  
Notifications by a form object to the client application are handled by the client application's **IMAPIViewAdviseSink** interface. For more information, see [IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md).
  

