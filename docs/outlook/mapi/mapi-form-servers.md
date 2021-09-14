---
title: "MAPI Form Servers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 855292b8-028e-4c1e-87ed-3f20b9ba584a
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Form Servers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
From the user's perspective, a form is usually a property sheet for a message or a data-entry form that enables users to enter structured information. However, it can be any user interface that is associated with a message class. From a programmer's point of view, a form consists of:
  
- A type of MAPI message with its own message class and OLE identifier.
    
- The executable file that implements the form server.
    
- A collection of MAPI properties — custom or otherwise — that the form server uses. Some or all of these may be available to messaging clients for use.
    
- The configuration file that describes the form and is used by the form manager.
    
Because forms are [IMessage](imessageimapiprop.md) objects, they exhibit properties and behavior that is consistent with MAPI message objects. However, because forms can have custom properties, controls, and a display rendering that is application-specific, the MAPI interfaces that forms use are generic enough to permit any sort of interface that is needed. The actual definition of a form is stored in a form library, which is discussed later in this section. 
  
> [!NOTE]
> More accurately, all messages are instances of MAPI forms. However, it is usually easier to think of custom forms as special cases of messages, since forms for composing and reading typical email messages are the most commonly used forms. The fact that all messages are really just forms gives custom forms the same status as any other message in the MAPI system. 
  
Every form has a set of properties, some of which are visible in the form's user interface. Usually, properties are matched to fields in the form's user interface. For example, a purchase order form might have the fields Item, Description, Price, Tax, and Subtotal. These fields are simply visual renderings of form properties of the same names. Clients ascertain which properties are supported by a particular message class through the [IMAPIFormInfo::CalcFormPropSet](imapiforminfo-calcformpropset.md) method, which is implemented by the MAPI form manager. 
  
Like basic messages, MAPI forms can contain all the standard message properties such as the sender, the intended recipient, and when the message was sent. Forms can also contain any number of custom properties that are specific to the form. For example a "Bug Report" form might contain custom properties for Bug Type, Bug Severity, and Product Version.
  
To create a form you must implement a form server. The form server is the executable file that is loaded when a messaging client needs to display a message that is the type supported by the form server. The form server in turn creates form objects as necessary to display specific messages and handle user interactions with those messages.
  
Every form server has a configuration file associated with it. This file contains information that describes the form server for the benefit of the form manager. The form manager uses this information when installing the form server into a form library.
  
For details on creating the parts of a form, see [Developing MAPI Form Servers](developing-mapi-form-servers.md).
  
Form servers adhere to the Component Object Model (COM). Form servers run as standalone executables, not as in-proc servers. For more information, see the COM and ActiveX Object Services section in the Windows SDK.
  
A unique class identifier (CLSID) identifies each form server. There is always a one-to-one mapping between a class identifier and its message class. This does not mean, however, that a form server can only work with messages of one message class. If no form server is available to service a message of a particular class, the form manager being used should attempt to find a form server for a message class higher in the message class hierarchy; the default form manager supplied with the Windows SDK does this. Such a form server will probably be able to render only a subset of the message's properties (the ones supported by the superclass), but it will be better than nothing. What happens when no matching form server is found at all is an implementation detail specific to the form manager being used; the default form manager does not open messages when this happens.
  
For more information, see [MAPI Message Classes](mapi-message-classes.md).
  
## See also



[MAPI Forms](mapi-forms.md)

