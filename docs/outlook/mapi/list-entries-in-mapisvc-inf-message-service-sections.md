---
title: "List Entries in MapiSvc.inf Message Service Sections"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f4f052d6-ef63-421a-9d8c-4f3c6df83863
description: "Last modified: July 23, 2011"
 
 
---

# List Entries in MapiSvc.inf Message Service Sections

  
  
**Applies to**: Outlook 
  
There are two types of section list entries: one that lists service provider sections and one that lists miscellaneous message service-specific sections. These two types of entries appear in mapisvc.inf using the following formats:
  
```cpp
Providersprovider section1, provider section2, ...... provider sectionX
Sectionssection name1, section name2, ......section nameX

```

Each section in the **Providers** entry maps to an individual section providing configuration information for a service provider that belongs to the message service. Each section in the **Sections** entry maps to a section that contains extra configuration information needed by the message service. Message service implementers define extra sections when they want to include special information that does not fit in the standard sections. Message services that have complicated configurations typically use the **Sections** entry to add extra information. Every message services section has a **Providers** entry with at least one section in the list; not all message service sections have a **Sections** entry. 
  
Two examples of message service sections follow. The first section is for the Default Address Book service from the earlier illustration, a straightforward message service with a single service provider. The second section is for the MsgService service, a more complex sample message service with three service providers. 
  
```cpp
[AB]
PR_DISPLAY_NAME=Default Address Book
Providers=AB Provider
PR_SERVICE_DLL_NAME=AB.DLL
PR_SERVICE_SUPPORT_FILES=AB.DLL
PR_SERVICE_ENTRY_NAME=DABServiceEntry
PR_RESOURCE_FLAGS=SERVICE_NO_PRIMARY_IDENTITY
[MsgService]
PR_DISPLAY_NAME=My Own Service
Providers=MsgService Prov1, MsgService Prov2, MsgService Prov3
Sections=First_Special_Section, Second_Special_Section
PR_SERVICE_DLL_NAME=MYSERV.DLL
PR_SERVICE_SUPPORT_FILES=MYSERV.DLL, MYXXX.DLL, MYZZZ.DLL
PR_SERVICE_ENTRY_NAME=MyServiceEntry
PR_RESOURCE_FLAGS=SERVICE_SINGLE_COPY
66040003=00000000

```

The **Sections** entry in the **[MsgService]** section lists two additional sections, one called **[First_Special_Section]** and the other called **[Second_Special_Section]**. The data that might appear in extra sections is meaningful to the specific message service. These sections appear following to illustrate extra sections. 
  
```cpp
[First_Special_Section]
UID=13DB0C8AA05101A9BB000AA002FC45A
66020003=01000000
66000003=00040000
66010003=06000000
66050003=03000000

```


