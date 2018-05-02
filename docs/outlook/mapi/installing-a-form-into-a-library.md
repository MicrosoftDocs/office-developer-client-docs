---
title: "Installing a Form into a Library"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 303c9dcb-f9b5-4cea-b5f2-3eba01aa3b09
description: "Last modified: July 23, 2011"
 
 
---

# Installing a Form into a Library

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
The default MAPI form manager supplied with the Windows SDK does not provide a user interface for installing forms in the various form libraries. Because of this, you will have to create a small application — or detailed set of instructions — that users can use to install the form.
  
If you implement an installation application, the series of actions it must perform to install a form into a folder's associated contents table are as follows:
  
1. Call the [MAPIOpenFormMgr](mapiopenformmgr.md) function to open the form manager. 
    
2. Use [IMAPIFormMgr::OpenFormContainer](imapiformmgr-openformcontainer.md) or [IMAPIFormMgr::SelectFormContainer](imapiformmgr-selectformcontainer.md) method to select and open the target container for the form. 
    
3. Use the [IMAPIFormContainer::InstallForm](imapiformcontainer-installform.md) function to install the form. 
    
    Steps 4 through 6 are for installation into a local form library:
    
4. Copy all files to the appropriate place on the local disk, if installation is to the local form library on the user's workstation. If necessary, modify the form configuration file to reflect current paths of components. The form configuration file can contain relative paths, in which case this step may not be necessary.
    
5. Complete the appropriate OLE registration steps to associate the message type with the form server being installed.
    
6. If the form was installed into the local form library, copy the form's icon (.ico) and configuration (.cfg) files into the %WINDOWS%\FORMS\CONFIGS directory so the form can be automatically restored in case the form library is corrupted or deleted. This step is recommended but not mandatory.
    
> [!NOTE]
> You can simplify installation to a local form library by replacing steps 1 and 2 with a call to the [MAPIOpenLocalFormContainer](mapiopenlocalformcontainer.md) function. 
  
## See also

#### Concepts

[Developing MAPI Form Servers](developing-mapi-form-servers.md)

