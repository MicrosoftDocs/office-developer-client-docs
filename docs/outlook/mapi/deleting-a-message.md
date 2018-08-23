---
title: "Deleting a Message"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 9ed166b4-6b7b-478f-bbe5-4115bb818ac0
description: "Last modified: July 23, 2011"
 
 
---

# Deleting a Message

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A client can delete a message when it is open and the user is reading it, or when it is closed and the user is viewing the contents table. To protect a user from inadvertently removing a message, MAPI defines message deletion as a two step process:
  
1. Mark a message for deletion by moving it to the folder that has been designated as the Deleted Items folder — the folder whose entry identifier is stored in the **PR_IPM_WASTEBASKET_ENTRYID** ([PidTagIpmWastebasketEntryId](pidtagipmwastebasketentryid-canonical-property.md)) property. 
    
2. Remove the message by calling the [IMAPIFolder::DeleteMessages](imapifolder-deletemessages.md) method. 
    
When a user chooses to delete a message in a folder other than the Deleted Items folder, mark it for deletion. Only when a user selects messages from within the Deleted Items folder should the messages be physically removed from the workstation. You can prompt the user to verify that the user really intended to perform the deletion.
  
 **To delete a message**
  
1. Confirm with the user that the impending deletion is intentional.
    
2. Determine the parent of the folder to be deleted. If it is the Deleted Items folder or a subfolder within the Deleted Items folder, call [IMAPIFolder::DeleteMessages](imapifolder-deletemessages.md) to remove the message. 
    
3. If the folder is not contained within the Deleted Items folder, call [IMAPIFolder::CopyMessages](imapifolder-copymessages.md) with the MESSAGE_MOVE flag set to relocate the message to the Deleted Items folder. 
    

