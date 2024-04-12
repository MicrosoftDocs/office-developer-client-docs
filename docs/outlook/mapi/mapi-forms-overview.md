---
title: "MAPI forms overview"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 1b3afeaa-4ede-41eb-a3c1-b8947a46ef97
---

# MAPI forms overview
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A MAPI form is a viewer for a message. Every message has a message class that dictates the particular form that is used as its viewer. MAPI defines several message classes and has implemented the forms for viewing messages of these classes. Client software developers can create new message classes and custom forms for viewing messages created by using the new classes.
  
Every custom form implements a set of standard menu commands, such as **Open**, **Create**, **Delete**, and **Reply**, and a set of commands that are specific to the particular form. Some of the form commands are integrated with the user interface of the client application when the form is active; other form commands completely replace the client commands. 
  
The following illustration shows the relationship between the MAPI components involved in using forms. 
  
**MAPI form architecture**
  
![MAPI form architecture](media/forms01.gif "MAPI form architecture")
  
In the diagram, notice that the form manager plays a role that is similar to other MAPI service providers, although it is not a service provider itself. The form manager is a replaceable DLL that implements some of the MAPI interfaces. Although developers can implement their own form manager, most environments will use the form manager provided by Microsoft due to the form manager's complexity.
  
The following list describes the components in the diagram and their relationship to other components:
  
- Messaging client: An application that can use form objects. The messaging client uses the MAPI form interfaces to communicate with the form manager to load messages into form objects.
    
- MAPI form interfaces: A defined standard for communication between MAPI components that are related to forms.
    
- Form manager: The DLL that messaging clients use to handle installation of forms in form libraries, loading of form servers, and initial communication between messaging clients and form servers.
    
- Form libraries: Permanent storage for the executable files associated with form servers.
    
- Form servers: Executable files that implement a form. Form servers create form objects and user interfaces to deal with specific messages. This executable is also an OLE server and adheres to the usual OLE conventions.
    
- Form objects: Run-time objects created by form servers that correspond to specific messages. Form objects run in the same process context as their form server.
    
For more information about MAPI form components, see [MAPI Forms](mapi-forms.md).
  
## See also

- [MAPI Features and Architecture](mapi-features-and-architecture.md)

