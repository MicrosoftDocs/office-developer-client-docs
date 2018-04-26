---
title: "HelpContext, HelpFile Properties (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 8a79f994-f17c-2983-0593-095801be762e

---

# HelpContext, HelpFile Properties (ADO)

Indicates the help file and topic associated with an [Error](error-object-ado.md) object. 
  
## Return Values

- **HelpContextID** — returns a context ID, as a **Long** value, for a topic in a Help file. 
    
- **HelpFile** — returns a **String** value that evaluates to a fully resolved path to a Help file. 
    
## Remarks

If a Help file is specified in the **HelpFile** property, the **HelpContext** property is used to automatically display the Help topic it identifies. If there is no relevant help topic available, the **HelpContext** property returns zero and the **HelpFile** property returns a zero-length string (""). 
  

