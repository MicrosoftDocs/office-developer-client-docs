---
title: "About Setting the Resolution Order for Address Lists in Outlook"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: e1589568-cb49-86dd-5d16-b08c8117bd17
description: "Last modified: July 05, 2012"
 
 
---

# About Setting the Resolution Order for Address Lists in Outlook

  
  
**Applies to**: Outlook 
  
For each profile, Microsoft Office Outlook supports multiple address lists and users can manually specify the order of address lists by which recipients in e-mail messages and attendees in meeting requests are resolved. For example, you can set the resolution order so that names are resolved first against your Outlook Address Book, and then against the Global Address List. On a computer, a user can open the Address Book, click **Tools** and then **Options** to specify this resolution order. However, in a corporate environment, it is more efficient for IT administrators to programmatically set the order of address lists by which names are resolved. Such code can be used as part of a startup automation script that an administrator deploys inside the corporation. 
  
MAPI supports the **[SetSearchPath](iaddrbook-getsearchpath.md)** method in the **[IAddrBook](iaddrbookimapiprop.md)** interface, which allows you to set a new search path in the profile that is used for name resolution. To use the **IAddrBook::SetSearchPath** method, you must specify the desired resolution order by using an array that holds containers of the relevant address books in the order they should be resolved. Each entry in that array should also contain the entry ID of the corresponding address book. 
  
The following are code examples of how to specify a custom search path for address lists.
  
- [How to: Programmatically Set the Resolution Order for Address Lists](how-to-programmatically-set-the-resolution-order-for-address-lists.md)
    
- [KB 292590: How To Change Address Book Sort Order with SetSearchPath](http://support.microsoft.com/kb/292590)
    

