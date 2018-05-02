---
title: "MAPI Form Objects"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: eb9107d9-ad5c-4264-a457-dea193597dc9
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Form Objects

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Form objects are created dynamically by form servers in order to display specific messages and allow users to interact with them. A form object is, therefore, an instantiation of the class derived from [IMAPIForm](imapiformiunknown.md) that is implemented by the form server. When a client application opens a message, the form server for that message class creates a form object to handle the message. The form object then creates its interface and displays the properties of the message in it. The form object and its interface persists until the user closes it. The form object handles any changes to the values of the message's properties. 
  
Additionally, the MAPI form interfaces define a mechanism by which one form object can load and display a series of messages. This is an efficiency mechanism, as it avoids needless destruction and creation of message objects and their interfaces. When requested by the messaging client to load a different message, the form object should save any changes to the current message's properties.
  
For information on a client application's perspective of form objects, see [MAPI Custom Form Objects](mapi-custom-form-objects.md).
  
## See also

#### Concepts

[MAPI Forms](mapi-forms.md)

