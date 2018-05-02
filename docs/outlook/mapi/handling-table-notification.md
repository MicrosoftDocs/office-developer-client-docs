---
title: "Handling Table Notification"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: edc9bc71-4885-4783-b465-0bafa20eff73
description: "Last modified: July 23, 2011"
 
 
---

# Handling Table Notification

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
As an alternative to registering directly with an advise source object, such as a folder or a messaging user, a client can register for notifications on a contents or hierarchy table. Tracking changes to address book entries, folders, and messages through a contents or hierarchy table can be simpler and more straightforward than through individual objects. For example, you can call [IMAPITable::Advise](imapitable-advise.md) on a folder's hierarchy table to discover when changes occur to one of its subfolders. If you support the viewing of remote messages, register with the status table to observe activity by transport providers and the MAPI spooler. 
  
However, it is not always preferable to use table notifications instead of object notifications. Monitoring changes in the number of messages in a folder is an example of when your client might need to register for object notifications on a folder rather than on a table implemented by the folder.
  

