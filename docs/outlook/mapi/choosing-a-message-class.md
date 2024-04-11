---
title: "Choosing a Message Class"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 5ca8edd2-41b7-40e2-b755-b28eecb49786
 
 
---

# Choosing a Message Class

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
As described in [MAPI Message Classes](mapi-message-classes.md), message classes are important for establishing the relationship between types of custom messages and, by extension, between form servers themselves. Fortunately, choosing a message class string is fairly simple. The message class string of a message class is an arbitrary string, but it should use the following conventions:
  
- The string should satisfy all the conventions described in the documentation for the **PR_MESSAGE_CLASS** ([PidTagMessageClass](pidtagmessageclass-canonical-property.md)) property. Importantly, the string must be composed entirely of ANSI characters and be less than 256 characters long.
    
- If your form server is derived from an existing form server or is an extension of an existing form server, your message class string should be formed by adding a period and another word to the message class string of the form server that your form is based on. For example, you might want to implement a form to reschedule a meeting, and your form is based on an existing form for scheduling meetings. If the meeting scheduling form's message class string is "IPM.Meeting", your message class string could be "IPM.Meeting.Reschedule".
    
- If your form is not based on any existing form, your message class string should still begin with either the "IPM." or "IPC." prefix, depending on whether the form is intended to be received by a person or by another application. "IPM." designates an interpersonal message that usually ends up in a user's Inbox, and "IPC." designates an interprocess communication message that is not typically delivered to a user's Inbox.
    
- If your message class is intended to be human-readable, the message class string should start with "IPM." A message class is generally considered human-readable if it uses any properties that contain plain text, HTML, or Rich Text Format (RTF) data. If your form uses the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property, it should almost certainly use an "IPM." message class string. For example, if you are implementing a form for purchase orders, and your organization requires that purchase orders be approved by a manager, your message class string could be "IPM.Purchase_Order". Forms that are designed for use with public folders or public folder applications are typically considered to be interpersonal because they are read by people even though they are not actually addressed to any person's email address. The typical prefix for public folder message classes is "IPM.Post". 
    
- If your message class is intended to be received by another application instead of by a person, the message class string should start with "IPC." For example, if you are implementing a form that enables people to automatically subscribe to mailing lists, your message class string could be "IPC.Subscribe".
    
- Your message class string should never end with a period.
    
The message class string should be put in the **[Description]** section of the form configuration file, in the **MessageClass** entry, similar to the following: 
  
 `MessageClass=IPM.Meeting.Reschedule`
  
After you have chosen an appropriate message class string, you should generate a class identifier for it. Class identifiers can be generated with the **Create GUID** command that is included in Visual Studio. The class identifier must be put in the form configuration file's **CLSID** entry, along with the **MessageClass** entry, similar to the following: 
  
 `CLSID={88FFF551-B8C5-11ce-8DE0-00AA0060D242}`
  
Your class identifier will almost certainly be different, of course. For more information, see [Creating a Form Configuration File](creating-a-form-configuration-file.md).
  
When the form is installed on a user's computer, your installation process — whether it is a setup program or something else — must make a registry entry in the **HKEY_CLASSES_ROOT\CLSID\** section of the registry for the class identifier. This entry must be set to the message class string. For example, you would create a registry entry similar to the following for the example class identifier above: 
  
 `HKEY_CLASSES_ROOT\CLSID\{88FFF551-B8C5-11ce-8DE0-00AA0060D242}="IPM.Meeting.Reschedule"`
  
For more information, see [Installing a Form into a Library](installing-a-form-into-a-library.md).
  
## See also



[Developing MAPI Form Servers](developing-mapi-form-servers.md)

