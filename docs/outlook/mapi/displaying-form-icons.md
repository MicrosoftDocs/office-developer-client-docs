---
title: "Displaying Form Icons"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 197e72ab-f9d6-4889-a677-0ce4c27b1aad
description: "Last modified: July 23, 2011"
 
 
---

# Displaying Form Icons

  
  
**Applies to**: Outlook 
  
When displaying a list of messages in a folder, it is helpful to your users if you distinguish messages with custom message classes from the standard IPM.Note messages. Custom message classes correspond to form servers, and form servers provide icons to represent themselves. You can display these icons in the list of messages to alert users to each message's message class before the user opens the messages. Typically, the icon in the form's **PR_MINI_ICON** ( [PidTagMiniIcon](pidtagminiicon-canonical-property.md)) property is the one that should be displayed in the list of messages. Forms also have a **PR_ICON** ( [PidTagIcon](pidtagicon-canonical-property.md)) property that can be displayed when the form is minimized in a property sheet.
  
 **To get an icon for a message class without activating the form server for that message class**
  
1. Call the [IMAPIFormMgr::OpenFormContainer](imapiformmgr-openformcontainer.md) method to get a pointer to an [IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md) interface. 
    
2. Call the [IMAPIFormContainer::ResolveMessageClass](imapiformcontainer-resolvemessageclass.md) method to get a pointer to an [IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md) interface. 
    
3. Call the [IMAPIFormInfo::MakeIconFromBinary](imapiforminfo-makeiconfrombinary.md) method to get an icon handle. 
    
The icon can then be displayed using standard Win32 APIs.
  
> [!IMPORTANT]
> Once you have the icon for a message class, make every effort to cache that icon. Not caching icons severely affects the performance of client applications. When caching icons, be careful of the relationships between message classes and their subclasses. For example, if the IPM.Note.Meeting.Cancel message class happens to resolve back to IPM.Note, do not assume that all subclasses of IPM.Note should use the icon for IPM.Note. 
  

