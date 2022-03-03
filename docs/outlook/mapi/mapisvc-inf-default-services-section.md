---
title: "MapiSvc.inf [Default Services] Section"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: dec42f8d-0f5c-4665-b53a-11cbc58b8b76
 
 
---

# MapiSvc.inf [Default Services] Section

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The **[Default Services]** section lists all of the message services that are selected as default message services. These default message services are a subset of the message services listed in the **[Services]** section. When a profile configuration program creates a default profile, the message services in this section are automatically included. 
  
The entries use the same format as entries in the **[Services]** section, as shown following: 
  
 **[Default Services]**
  
 _message-service section name_ =  _message service name_
  
The following entries would be included in the **[Default Services]** section for the mapisvc.inf shown in the earlier illustration: 
  
```cpp
[Default Services]
AB=Default Address Book
MsgService=My Own Service

```


