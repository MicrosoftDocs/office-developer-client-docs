---
title: "Retrieving Form Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 9dec5ad6-af34-4c5e-848b-5c3909d0c0a1
description: "Last modified: July 23, 2011"
 
 
---

# Retrieving Form Properties

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
To issue a query that is meaningful to a custom message type, an application needs to know the properties that are expected on that message. To get a list of properties that a custom message class uses, a client application queries the MAPI form manager. The form manager gets this information from the appropriate form configuration file so that client applications can use this information without the overhead of activating the form server itself. To do this, the client application calls the [IMAPIFormMgr::ResolveMessageClass](imapiformmgr-resolvemessageclass.md) method as follows: 
  
```
IMAPIFormInfo *pfrminf = NULL;
hr = pfrmmgr->ResolveMessageClass("IPM.Demo", 0L, NULL, &amp;pfrminf);

```

Note that the third argument to **ResolveMessageClass** is the folder that contains the associated contents table that the query will search for form servers. NULL indicates that the form manager should search all available form containers. If the query is to run against a particular folder, it is better to include the appropriate [IMAPIFolder](imapifolderimapicontainer.md) pointer instead. 
  
## See also

#### Concepts

[Form Server Interactions](form-server-interactions.md)

