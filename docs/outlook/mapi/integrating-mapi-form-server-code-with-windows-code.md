---
title: "Integrating MAPI Form Server Code with Windows Code"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 47ec3e97-ad2b-43ea-842a-b2a0675eef48
description: "Last modified: July 23, 2011"
 
 
---

# Integrating MAPI Form Server Code with Windows Code

  
  
**Applies to**: Outlook 
  
Recall that your form server is a Win32 application. As such, there are some tasks related to loading your form server into memory and exiting cleanly. Like all Windows applications, the entry point for your form server is the **WinMain** function. This function is the appropriate place to perform the following tasks: 
  
- Creating and registering a window class so that your form server can interact with other OLE components.
    
- Creating and registering a window class or classes for your form objects' user interfaces.
    
- Calling the [MAPIInitialize](mapiinitialize.md) function. **MAPIInitialize** handles the required OLE initialization for you, as well. This must be done once per instance of your form server. 
    
- Registering a global atom with a string representation of the form server's class identifier (CLSID). This atom should exist for the lifetime of the form server.
    
- Calling the OLE function [CoRegisterClassObject](http://msdn.microsoft.com/en-us/library/ms693407.aspx) to register your form server's class factory with OLE. 
    
- Creating a main window to receive messages. This window probably does not need to be visible because the user will be interacting with the specific windows associated with individual form objects. However, during development, the main window can be a convenient place for debugging output or control of your form server.
    
- Creating a message loop that runs for the lifetime of the form server, translating and dispatching windows messages to active form objects.
    
When your form server exits, it should perform the following tasks:
  
- Call the OLE function [CoRevokeClassObject](http://msdn.microsoft.com/en-us/library/ms688650%28VS.85%29.aspx) to revoke your message class's OLE registration. 
    
- Call **MAPIUninitialize** to properly close the form server's connection to MAPI. 
    
- Delete the global atom that contains the string representation of the class identifier.
    
## See also



[Writing Form Server Code](writing-form-server-code.md)

