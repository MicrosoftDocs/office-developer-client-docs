---
title: "Loading a Message Into a Form"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 4bdbe021-d694-4967-a105-4b24f1eebc44
description: "Last modified: July 23, 2011"
 
 
---

# Loading a Message Into a Form

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
To load an existing message into a form using a form server, use one of the following strategies.
  
- Call [IMAPISession::PrepareForm](imapisession-prepareform.md) to create a token and then [IMAPISession::ShowForm](imapisession-showform.md) to display the form. 
    
- Call [IMAPIFormMgr::LoadForm](imapiformmgr-loadform.md). 
    
Using the **PrepareForm** and **ShowForm** strategy is comparatively easy, but it results in forms that are modal with respect to your client. This is because the call to **ShowForm** does not return until the form has exited. If you need to handle forms asynchronously, do not use this strategy. 
  
Using the **LoadForm** strategy is more difficult because the method requires several parameters. These parameters instruct the form manager to launch the proper form server in the proper context and display the proper message. If the form server is already running, the form manager loads the message into the form server without launching a new instance of the form server. 
  
To specify which form server to launch, pass the message class handled by the target server in the contents of the  _lpszMessageClass_ parameter. The appropriate message class can be determined by retrieving the **PR_MESSAGE_CLASS** ( [PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property of the message to be loaded. Sometimes there is no form server for the specified message class, only a form server that handles messages belonging to the message's superclass. If you prefer that the message be loaded only by a form server specifically meant to handle messages of that class, set the MAPIFORM_EXACTMATCH flag in the **LoadForm** call. For more information, see [MAPI Message Classes](mapi-message-classes.md).
  
 **LoadForm** also requires a pointer to your viewer's message site and view context and the value for the target message's **PR_MSG_STATUS** ( [PidTagMessageStatus](pidtagmessagestatus-canonical-property.md)) and **PR_MESSAGE_FLAGS** ( [PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) properties.
  

