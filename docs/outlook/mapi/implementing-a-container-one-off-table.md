---
title: "Implementing a Container One-Off Table"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: eabbde74-49a1-4eeb-a01d-67e45ae4b343
description: "Last modified: July 23, 2011"
 
 
---

# Implementing a Container One-Off Table

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
To access the one-off table belonging to one of your containers, MAPI calls the container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to open the **PR_CREATE_TEMPLATES** ( [PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property with the **IMAPITable** interface. Your container is asked to return its one-off table when a client application is trying to add a recipient to the container. If the container allows any recipients, your provider can either return its own table implementation or call [IMAPISupport::GetOneOffTable](imapisupport-getoneofftable.md) to return the MAPI implementation. 
  
The set of templates in the container one-off table should reflect the type of recipients that the particular container can hold. Typically, this includes one or two templates, templates for creating an individual messaging user or a distribution list. The entry identifiers for these templates are held in the **PR_DEF_CREATE_MAILUSER** ( [PidTagDefCreateMailuser](pidtagdefcreatemailuser-canonical-property.md)) and **PR_DEF_CREATE_DL** ( [PidTagDefCreateDl](pidtagdefcreatedl-canonical-property.md)) properties. However, containers are by no means limited to these types of entries. They can hold other types of recipients or non-recipient entries such as directories. 
  

