---
title: "Form storage"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 6ddf9158-3c10-408a-aeaf-5a382c4339e7
---

# Form storage

**Applies to**: Outlook 2013 | Outlook 2016 
  
Although it is not necessary to know all the details of how forms are physically stored, it is useful to understand a few of the main concepts. Therefore, before describing the three types of form libraries supported by the default form manager, this topic gives an overview of how forms are stored.
  
Form definitions can be physically stored within folders in one or more MAPI message stores. Every MAPI folder can be thought of as having two areas for storing message objects: the standard part and the associated part. The standard part of the folder includes the messages and folders that users manipulate.
  
The associated part includes hidden message objects that are associated with the folder, including form definitions, views, rule templates, reply templates, and so on. This alternate part is called the folder-associated contents table, and the set of messages in the associated contents table is referred to as the folder-associated information. The hidden messages are an integral part of the folder and are copied along with the standard folder contents when the folder is copied. Although physically stored as messages, information in a folder's associated contents table behaves more like properties than like viewable messages. Any folder object that supports an associated contents table is capable of storing custom forms. The [IMAPIContainer::GetContentsTable](imapicontainer-getcontentstable.md) method can return either the standard contents or the associated contents of the folder, depending on the value of the method's  _ulflags_ parameter. 
  
A form library consists of form definitions stored in a folder's associated contents table. The form definition includes the form's properties, the actions the form supports, and even the form server executable file, which is stored as one or more message attachments.
  
Additionally, forms can be stored in any file or location that the form manager being used supports. The default form manager stores form servers in MAPI folders, but a custom form manager could implement its own storage for form servers.
  
A form can have multiple user interfaces that are bound to its message class. For example, a form can have separate Compose and Read user interfaces. The form takes care of invoking the proper user interface for different user requests, depending on which of the form's verbs is being called. For example, if your form server has separate composing and reading user interfaces, the Compose user interface can be opened automatically when the user creates a new message of the form's message class and the Read user interface can be opened automatically when the user opens an existing message of the form's message class.
  
Most of the information stored within a form definition is available by invoking the [IMAPIFormInfo::IMAPIProp](imapiforminfoimapiprop.md) method on an **IMAPIFormInfo** object. The **IMAPIFormInfo** interface simplifies access to form information by calling all the MAPI folder and message methods needed to retrieve the information. An **IMAPIFormInfo** object can be obtained by calling the [IMAPIFormContainer::ResolveMessageClass](imapiformcontainer-resolvemessageclass.md) method. 
  
The three types of form libraries are described in the topics [Local Form Libraries](local-form-libraries.md), [Folder Form Libraries](folder-form-libraries.md) and [Personal Form Libraries](personal-form-libraries.md).
  
## See also

- [MAPI Forms](mapi-forms.md)

