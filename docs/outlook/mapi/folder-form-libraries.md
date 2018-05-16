---
title: "Folder Form Libraries"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 62b7480e-b3eb-45fb-b74d-62f1dc918a53
description: "Last modified: July 23, 2011"
 
 
---

# Folder Form Libraries

  
  
**Applies to**: Outlook 
  
In some cases, you might want to associate one or more forms with a specific folder. For example, employees in your organization could all have a Progress Report folder in their personal message store for creating and storing progress reports. Because the progress report is specific to each user's Progress Report folder, it might not be appropriate to store the progress report form in the system wide form library. However, a copy of the progress report form can be kept in the associated-contents table of each user's Progress Report folder. This restricts the user from using progress report forms outside of the designated folder.
  
Conceptually, there is one folder form library for every folder in a message store, even if no form servers are installed in it. Folder form libraries are implemented like other form libraries — they are stored as associated-contents tables in the alternate part of the folder. Because folder form libraries are contained in the folder, they are copied along with their parent folder in copy operations.
  
## See also

#### Concepts

[MAPI Forms](mapi-forms.md)

