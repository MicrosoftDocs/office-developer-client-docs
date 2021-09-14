---
title: "About the Sample Offline State Add-in"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: a6bdf408-114a-2203-189f-101251a65a8c
description: "Last modified: July 23, 2011"
 
 
---

# About the Sample Offline State Add-in

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The Offline State API supports callbacks indicating changes in a user's connection state in Outlook—for example, from being online in Outlook to being offline. The Sample Offline State Add-in is a COM add-in written in C++ that demonstrates how to receive notifications of connection state changes and how to modify the current state using the Offline State API. For more information about the Offline State API, see [About the Offline State API](about-the-offline-state-api.md).
  
## In this section

- [Installing the Sample Offline State Add-in](installing-the-sample-offline-state-add-in.md)
    
- Explains how to download and install the Sample Offline State Add-in.
    
- [Setting Up an Offline State Add-in](setting-up-an-offline-state-add-in.md)
    
- Describes how to implement connection, initialization, and setup functions in order to use an offline state add-in.
    
- [Monitoring Connection State Changes Using an Offline State Add-in](monitoring-connection-state-changes-using-an-offline-state-add-in.md)
    
- Describes how to use the **[HrOpenOfflineObj](hropenofflineobj.md)** function to obtain an offline object to monitor and change the connection state. 
    
- [Disconnecting an Offline State Add-in](disconnecting-an-offline-state-add-in.md)
    
- Describes how to properly terminate and clean up an offline state add-in when the add-in is disconnected.
    
## See also



[About the Offline State API](about-the-offline-state-api.md)

