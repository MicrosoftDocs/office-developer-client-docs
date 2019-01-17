---
title: Exchange users
TOCTitle: Exchange users
ms:assetid: 01802032-fd60-400b-ad83-1f4eefe596bd
ms:mtpsurl: https://msdn.microsoft.com/library/Ff184585(v=office.15)
ms:contentKeyID: 55119835
ms.date: 07/24/2014
mtps_version: v=office.15
localization_priority: Normal
---

# Exchange users

This section provides sample tasks that involve Microsoft Exchange mailbox users. Exchange users are connected to an Exchange server, and are represented by [ExchangeUser](https://msdn.microsoft.com/library/bb609574\(v=office.15\)) objects, which are derived from the [AddressEntry](https://msdn.microsoft.com/library/bb609728\(v=office.15\)) object.

## In this section

|Topic|Description|
|:----|:----------|
|[Get information about the current user](how-to-get-information-about-the-current-user.md)  |Gets the current user’s information, such as name, job title, and telephone number.|
|[Get information about all distribution lists of which the current user is a member](how-to-get-information-about-all-distribution-lists-of-which-the-current-user-is-a-member.md)  |Uses the [GetMemberOfList()](https://msdn.microsoft.com/library/bb623397\(v=office.15\)) method to get information about all distribution lists of which the current user is a member.|
|[Create a distribution list](how-to-create-a-distribution-list.md)  |Creates a distribution list and displays it to the user.|
[Get members of an Exchange distribution list](how-to-get-members-of-an-exchange-distribution-list.md)  |Prompts the user to select an Exchange distribution list from the **Select Names** dialog box and expands the distribution list to display its members.|
[Get information about the current user's manager](how-to-get-information-about-the-current-user-s-manager.md)  |Gets information (such as name, job title, and phone numbers) about the current user’s manager.|
[Get availability information for an Exchange user's manager](how-to-get-availability-information-for-an-exchange-user-s-manager.md) |  Displays the next free 60-minute time slot in the calendar for a user's manager.|
|[Check a manager's response to a meeting request](how-to-check-a-manager-s-response-to-a-meeting-request.md) | Uses the [GetExchangeUser()](https://msdn.microsoft.com/library/bb611808\(v=office.15\)) and [GetExchangeUserManager()](https://msdn.microsoft.com/library/bb646656\(v=office.15\)) methods to check the status of the response of the current user's manager to a meeting request.|
|[Get information about direct reports of the current user's manager](how-to-get-information-about-direct-reports-of-the-current-user-s-manager.md) | Gets the direct reports of the current user’s manager, if any, and then displays information about each of the manager’s direct reports.|

## See also

- [Accounts](accounts.md)
- [Address book](address-book.md)
- [Stores](stores.md)
- [How do I... (Outlook 2013 PIA reference)](how-do-i-outlook-2013-pia-reference.md)

