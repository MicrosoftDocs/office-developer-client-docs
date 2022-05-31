---
title: "MAPI Form Interfaces"
description: This article provides links and descriptions to the different MAPI form interfaces and methods with additional notes.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 611213c9-e758-4366-b193-fc62181d3d1f
---

# MAPI Form Interfaces

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI defines the following interfaces relating to forms.
  
|**Interface name**|**Description**|
|:-----|:-----|
|[IMAPIForm](imapiformiunknown.md) <br/> |Manipulates form objects and handles form object commands. |
|[IMAPIFormAdviseSink](imapiformadvisesinkiunknown.md) <br/> |Determines if the form object can handle the next message and changes the next or previous state of the form object. |
|[IMAPIFormContainer](imapiformcontaineriunknown.md) <br/> |Supports installation, deinstallation, and resolution of form servers against a specific form container. |
|[IMAPIFormFactory](imapiformfactoryiunknown.md) <br/> |Supports the use of configurable run-time form servers. |
|[IMAPIFormInfo](imapiforminfoimapiprop.md) <br/> |Enables client applications to work with properties that are specific to a message class. |
|[IMAPIFormMgr](imapiformmgriunknown.md) <br/> |Enables client applications to get information about form servers, activates form servers, and installs form servers in the messaging system. |
|[IMAPIMessageSite](imapimessagesiteiunknown.md) <br/> |Used to manipulate messages associated with form objects. |
|[IMAPIViewAdviseSink](imapiviewadvisesinkiunknown.md) <br/> |Notifies client applications that an event has occurred in the form object. |
|[IMAPIViewContext](imapiviewcontextiunknown.md) <br/> |Used to respond to Next, Previous, and Delete commands in the form object. |
|[IPersistMessage](ipersistmessageiunknown.md) <br/> |Used to save, initialize, and load form objects to and from message storage. |
   
For more information about the methods of the MAPI form interfaces, see the documentation for these interfaces. You do not have to implement all of the MAPI form interfaces in order to create a custom form. A form itself requires only that you implement the **IPersistMessage**, **IMAPIForm**, and **IMAPIFormAdviseSink** interfaces. Additionally, it is also a good idea to implement **IMAPIFormFactory** and **IMAPIFormInfo**. **IMAPIFormFactory** is useful for OLE compliance, and **IMAPIFormInfo** enables well-written client applications to make better use of your forms. 
  
> [!NOTE]
> Strictly speaking, **IMAPIFormAdviseSink** is an optional interface. However, it is strongly recommended that you implement it in your form servers. This interface is critical to efficient interaction between messaging clients and form servers, especially when several messages of your form server's message class are being dealt with. 
  
## See also



[MAPI Forms](mapi-forms.md)

