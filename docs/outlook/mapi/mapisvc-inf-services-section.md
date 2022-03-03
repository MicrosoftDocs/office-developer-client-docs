---
title: "MapiSvc.inf [Services] Section"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 99f8e623-3138-4def-9778-5580326111a5
 
 
---

# MapiSvc.inf [Services] Section

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The **[Services]** section lists the message services that are installed on a computer. Entries in this section use the following format: 
  
 **[Services]**
  
 _message-service section name_ =  _message service name_
  
The message-service section name is a string defined by the message service that links this entry to a corresponding section for the service elsewhere in mapisvc.inf. The message service name is the name of the installed service. The following section shows three message services: the Default Address Book, My Own Service, and the Message Store Service. These services are fictional, for illustration purposes only. Each message service implementer would substitute the appropriate entry for his or her message service in this section.
  
```cpp
[Services]
AB=Default Address Book
MsgService=My Own Service
MS=Message Store Service

```

Each entry in this section has a corresponding section of its own where information for the message service is stored. For example, the corresponding section for the Default Address Book is called [AB].
  

