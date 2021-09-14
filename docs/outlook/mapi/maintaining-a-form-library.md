---
title: "Maintaining a Form Library"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 8488f7ec-e44b-4d1a-ba42-baea8c71d350
description: "Last modified: July 23, 2011"
 
 
---

# Maintaining a Form Library

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A form library holds all of the important information about a form: its properties, its verbs, and its server's executable files. Some clients allow their users to maintain, install, or remove form servers. If you want to offer this feature to your users, you must have access to:
  
- The form server's configuration file, a file with the .CFG extension.
    
- The form library's container object, an object that implements the [IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md) interface. 
    
To access the configuration file or a pathname to it, use whatever means are convenient. Usually, clients present the user with a dialog box for installing and removing form servers that can also be used to prompt the user for the location of the configuration file.
  
To access the form library's container, call the form manager's [IMAPIFormMgr::OpenFormContainer](imapiformmgr-openformcontainer.md) method. Pass in an enumeration value to specify which form library to open, and if necessary, a pointer to the object that the form manager should use to open the form library. For example, if you are opening a [Folder Form Libraries](folder-form-libraries.md), pass an [IMAPIFolder : IMAPIContainer](imapifolderimapicontainer.md) pointer. 
  
After **OpenFormContainer** returns the **IMAPIFormContainer** pointer, call either [IMAPIFormContainer::InstallForm](imapiformcontainer-installform.md) or [IMAPIFormContainer::RemoveForm](imapiformcontainer-removeform.md), depending on the maintenance to be performed. **InstallForm** adds a form server to the library; **RemoveForm** deletes a form server from the library. 
  

