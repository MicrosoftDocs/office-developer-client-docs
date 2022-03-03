---
title: "Starting a MAPI Session"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 7935ebed-f252-482c-ad8c-757aa2d8501d
 
 
---

# Starting a MAPI Session

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Although there is a significant amount of work performed during session start up, the required tasks are minimal. Much of this work is done in the MAPI processing of the [MAPIInitialize](mapiinitialize.md) and [MAPILogonEx](mapilogonex.md) calls. Both of these functions accept flags as input parameters for controlling aspects of the session such as notification handling and the user interface. It is important to understand the consequences of setting each of these flags when calling **MAPIInitialize** to initialize the MAPI libraries and **MAPILogonEx** to log on to the MAPI subsystem. 
  
 **To start a MAPI session**
  
1. Call **MAPIInitialize** to initialize the standard set of MAPI libraries. 
    
2. If you need to use the OLE libraries, call the OLE function [OleInitialize](https://msdn.microsoft.com/library/9a13e7a0-f2e2-466b-98f5-38d5972fa391%28Office.15%29.aspx).
    
3. If you need to use the MAPI utility library, call [ScInitMapiUtil](scinitmapiutil.md).
    
4. Call **MAPILogonEx** with a valid profile to log on to the MAPI subsystem. **MAPILogonEx** verifies the configuration of each of the service providers in the message services included in the profile, prompting the user for additional information if necessary and possible. When **MAPILogonEx** completes, the configured service providers are ready for service. 
    
## In this section

[Initializing MAPI](initializing-mapi.md)
  
> Describes how to initialize MAPI for a session.
    
[Initializing OLE for MAPI](initializing-ole-for-mapi.md)
  
> Describes the calls to make to initialize OLE for use with MAPI.
    
[Initializing the MAPI Utilities](initializing-the-mapi-utilities.md)
  
> Describes how to initialize MAPI utilities.
    
[Logging on to MAPI](logging-on-to-mapi.md)
  
> Describes how client applications log on to the MAPI sub system.
    

