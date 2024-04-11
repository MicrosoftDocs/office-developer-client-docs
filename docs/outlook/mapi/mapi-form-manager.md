---
title: "MAPI Form Manager"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: c0bbbd06-d47d-45ad-8179-2372d1d023d0
 
 
---

# MAPI Form Manager

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A form manager is an object that implements the [IMAPIFormMgr](imapiformmgriunknown.md) interface. Most organizations will use the form manager supplied with MAPI, referred to as the default form manager. However, an organization can replace the default form manager with a custom form manager if desired. The form manager takes care of locating forms within form libraries, loading forms in response to user requests, and installing forms into a user's local form library, folder form library, or personal form library. 
  
For a user to interact with a message, an instance of the form server for the message's message class must be created and activated to display the message and carry out the requested operation on the message. As described in the topic [MAPI Form Libraries](mapi-form-libraries.md), a form's implementation can exist in several different locations (form libraries) and there is no guarantee that a form or its server will be locally available or in a running state when a user wants to interact with it. The form manager takes care of the details of locating and activating the form.
  
Clients use services provided by the form manager to find and activate forms. The **IMAPIFormMgr** interface is implemented by the form manager and is called by clients to access its services. The form manager is an essential component because it hides almost all the details of finding and activating forms from messaging clients. 
  
When loading form servers, the default form manager loads the form from the first form library in which an implementation for the form's message class is found. The default form manager searches the form libraries in the following order:
  
1. The user's local form library. This form library is searched first because it provides the fastest access to a form's implementation if the implementation is installed in the local form library.
    
2. The folder form library of the message's container — the folder in which the message being loaded is stored.
    
3. The user's personal form library.
    
A custom form manager can search the available form libraries in any order, or can implement other form libraries such as an organization-wide form library. For more details on form libraries, see [MAPI Form Libraries](mapi-form-libraries.md). 
  
## See also



[MAPI Forms](mapi-forms.md)

