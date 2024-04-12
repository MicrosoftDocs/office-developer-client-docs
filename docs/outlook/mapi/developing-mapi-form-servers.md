---
title: "Developing MAPI Form Servers"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 30672a2d-2d39-4292-b21a-97a38485d1de
 
 
---

# Developing MAPI Form Servers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This section describes the process of creating form server executable and form configuration files for creating custom MAPI forms. Before reading this section, you should familiarize yourself with the information in [MAPI Forms](mapi-forms.md).
  
Developing a form server includes the following steps:
  
1. Deciding what information the form will contain and choosing a set of properties to hold that information. For more information, see [Choosing a Form's Property Set](choosing-a-form-s-property-set.md).
    
2. Designing a user interface with which users can interact with the form's properties.
    
3. Choosing a message class and generating a unique class identifier (CLSID). For an overview of message classes, see [MAPI Message Classes](mapi-message-classes.md). For more information about message classes and forms, see [Choosing a Message Class](choosing-a-message-class.md).
    
4. Implementing the required MAPI form interfaces, as well as any optional interfaces that your particular form server needs. For more information, see [Writing Form Server Code](writing-form-server-code.md). 
    
5. Writing user interface code to handle the user's interaction with the form object and the properties the form uses.
    
6. Creating a form configuration file for the form. For more information, see [File Format of Form Configuration Files](file-format-of-form-configuration-files.md).
    
7. Installing the form on users' computers. For more information, see [Installing a Form into a Library](installing-a-form-into-a-library.md).
    
You will most likely perform steps 1 through 5 simultaneously rather than completing them in sequence. The process of developing a form server, like many programming projects, is not one in which there is a particularly well-defined sequence. For example, creating a form configuration file is shown as the second-to-last step above, but you will probably create your form configuration file incrementally, and it will become more complete as you add features to your form server.
  
## See also



[MAPI Concepts](mapi-concepts.md)

