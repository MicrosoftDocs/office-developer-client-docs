---
title: "Composing a New Message by Using a Form"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: c92181c4-79ca-4310-8bf1-2bc335c8e0cd
description: "Last modified: July 23, 2011"
 
 
---

# Composing a New Message by Using a Form

  
  
**Applies to**: Outlook 
  
To use a form to compose a new message, first create a new custom message object.
  
 **To compose a new message using a form**
  
1. Call the form manager's [IMAPIFormMgr::ResolveMessageClass](imapiformmgr-resolvemessageclass.md) method to retrieve a pointer to a form information object — an object that implements the [IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md) interface. 
    
2. Pass the pointer to the form information object in a call to [IMAPIFormMgr::CreateForm](imapiformmgr-createform.md). **CreateForm** loads the appropriate form server. In addition, pass an interface identifier to **CreateForm** to specify the interface to be used to access the new message. Typically, you request [IPersistMessage : IUnknown](ipersistmessageiunknown.md) by passing IID_IPersistMessage to **CreateForm**.
    
3. Save the new message by calling its [IPersistMessage::Save](ipersistmessage-save.md) method. The form server should set values for the message's required properties when it creates the message. 
    
4. Load the message by using one of two strategies: [IMAPIFormMgr::LoadForm](imapiformmgr-loadform.md) or [IMAPISession::PrepareForm](imapisession-prepareform.md) followed by [IMAPISession::ShowForm](imapisession-showform.md). For more information about these strategies, see [Loading a Message Into a Form](loading-a-message-into-a-form.md).
    
> [!NOTE]
> There are opportunities for performance gains when loading a new custom message into a form server because you will already have had an opportunity to get some information about the message — such as its message class — during the processing required for the **ResolveMessageClass** and **CreateForm** calls. Because of this, you will be able to simplify the processing required before calling **LoadForm** over that described in the topic [Loading a Message Into a Form](loading-a-message-into-a-form.md). 
  

