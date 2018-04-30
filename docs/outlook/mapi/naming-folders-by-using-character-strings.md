---
title: "Naming Folders by Using Character Strings"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: ec3c023b-7c99-489c-8217-78b303dc10df
description: "Last modified: July 23, 2011"
---

# Naming Folders by Using Character Strings

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
If you access one or more folders frequently during a session, consider assigning names to the folders with the [IMsgStore::SetReceiveFolder](imsgstore-setreceivefolder.md) method. Although **IMsgStore::SetReceiveFolder** is used primarily to establish special folders to receive incoming messages for particular message classes, it can also be used to associate any folder with a name. The name can be the same as the message class or it can be any character string, customized for your client's use. Associating a name with a folder decreases the time it takes to find and open the folder. 
  

