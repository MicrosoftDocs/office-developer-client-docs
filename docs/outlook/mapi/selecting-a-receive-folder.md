---
title: "Selecting a Receive Folder"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 144c7179-b390-479f-a2aa-324974f04eba
description: "Last modified: July 23, 2011"
 
 
---

# Selecting a Receive Folder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A receive folder is where incoming messages of a particular class are placed. For IPM and related report messages, MAPI assigns the Inbox as the default receive folder. For IPC and related report messages, MAPI assigns the root folder of the message store as the default receive folder. You can change these assignments or make additional assignments for other message classes. Making explicit receive folder assignments for your client's supported message classes is optional.
  
When an incoming message class does not have an assigned receive folder, the message store provider automatically uses the receive folder for the class that matches the longest possible prefix of the incoming class. For example, if your client receives a message of class IPM.Note.MyDocument and the only receive folder that has been established is the Inbox for IPM messages, this message will be placed in the Inbox because IPM.Note.MyDocument derives from the base class IPM.
  
When you are assigning a receive folder for IPC messages, never use a folder from the IPM subtree. These folders should be reserved for IPM messages only. Use instead a folder that is contained within the message store's root folder. 
  
 **To create a receive folder for an IPM message class**
  
1. Call the message store's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the **PR_IPM_SUBTREE_ENTRYID** ([PidTagIpmSubtreeEntryId](pidtagipmsubtreeentryid-canonical-property.md)) property. 
    
2. Call [IMsgStore::OpenEntry](imsgstore-openentry.md) with **PR_IPM_SUBTREE_ENTRYID** as the entry identifier to open the root folder of the IPM subtree in the message store. 
    
3. Call [IMAPIFolder::CreateFolder](imapifolder-createfolder.md) to create the receive folder. 
    
4. Call [IMsgStore::SetReceiveFolder](imsgstore-setreceivefolder.md) to map the new folder to your IPM message class. 
    
 **To create a receive folder for an IPC message class**
  
1. Call [IMsgStore::OpenEntry](imsgstore-openentry.md) with a null entry identifier to open the root folder of the message store. 
    
2. Call [IMAPIFolder::CreateFolder](imapifolder-createfolder.md) to create the receive folder. 
    
3. Call [IMsgStore::SetReceiveFolder](imsgstore-setreceivefolder.md) to map the new folder to your IPC message class. 
    
Assign the receive folder that you use for messages for related report messages. For example, if your client receives IPM.Note messages, set up one receive folder for future IPM.Note messages and the same receive folder for future Report.IPM.Note messages.
  

