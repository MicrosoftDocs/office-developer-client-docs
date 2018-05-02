---
title: "Welcome to the Outlook Auxiliary Reference"
manager: soliver
ms.date: 9/10/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 2e48a625-b3f7-9fd0-253e-fe12a1aca446
description: "The Outlook Auxiliary Reference contains conceptual content and reference documentation for four sets of APIs, code samples, and a redistributable installer that allow developers to extend and integrate with Outlook. APIs in this reference are exposed by Outlook for extensibility, outside of the Outlook object model."
 
 
---

# Welcome to the Outlook Auxiliary Reference

The Outlook Auxiliary Reference contains conceptual content and reference documentation for four sets of APIs, code samples, and a redistributable installer that allow developers to extend and integrate with Outlook. APIs in this reference are exposed by Outlook for extensibility, outside of the Outlook object model. 
  
If you are new to developing solutions for Outlook, see [Selecting an API or technology for developing solutions for Outlook](selecting-an-api-or-technology-for-developing-solutions-for-outlook.md) to identify the APIs and technologies that are most appropriate for your needs. For specific information about the Outlook object model, see the [Outlook VBA reference](http://msdn.microsoft.com/library/75e4ad96-62a2-49d2-bc51-48ceab50634c%28Office.15%29.aspx). For specific information on Messaging API (MAPI) supported by Outlook, see the [Outlook MAPI Reference](http://msdn.microsoft.com/library/3d980b86-7001-4869-9780-121c6bfc7275%28Office.15%29.aspx).
  
The conceptual discussion includes the following subjects:
  
- [About anti-spam settings](about-anti-spam-settings.md)
    
- [Managing message downloads for POP3 accounts](managing-message-downloads-for-pop3-accounts.md)
    
- [Locating the message download history for a POP3 account](locating-the-message-download-history-for-a-pop3-account.md)
    
- [Parsing the message download history for a POP3 account](parsing-the-message-download-history-for-a-pop3-account.md)
    
- [About conflict resolution for custom item types](about-conflict-resolution-for-custom-item-types.md)
    
- [About the last update time of an Offline Address Book](about-the-last-update-time-of-an-offline-address-book.md)
    
- [About registering a new domain for automatic configuration](about-registering-a-new-domain-for-automatic-configuration.md)
    
- [About meeting requests as informational updates and full updates](about-meeting-requests-as-informational-updates-and-full-updates.md)
    
- [About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md) (There is also a redistributable installer for third-party calendar rebasing tools, which works for previous versions of Outlook as well, since Outlook 2010. To download the installer, see [Outlook 2010: Auxiliary Reference Redistributable Installer and Header File for Rebasing Calendars](http://www.microsoft.com/downloads/details.aspx?FamilyID=77748863-4352-4b99-ae57-1d4ae803983b).)
    
- [About persisting TZDEFINITION to a stream to commit to a binary property](about-persisting-tzdefinition-to-a-stream-to-commit-to-a-binary-property.md)
    
The reference content includes the following:
  
- The [APIs Exported by Outlook](about-apis-exported-by-outlook.md) include functions and data structures that were originally implemented for internal use and are now exposed for public use. 
    
- The [Account Management API](about-the-account-management-api.md) provides access to user account information and notifications of account changes. 
    
- The [Data Degradation Layer API](about-the-data-degradation-layer-api.md) supports clients that access an Outlook item in a preferred character format rather than the object's native character format. 
    
- The [Free/Busy API](about-the-free-busy-api.md) provides free/busy status information about specific user accounts within a specific time range. 
    
- Sample how-to tasks in the Outlook Auxiliary Reference include the following:
    
  - [How to: Determine whether an Outlook item has been modified but not saved (Outlook Auxiliary Reference)](how-to-determine-whether-an-outlook-item-has-been-modified-but-not-saved-outlook.md)
    
  - [How to: Parse a stream from a binary property to read the TZDEFINITION structure](how-to-parse-a-stream-from-a-binary-property-to-read-the-tzdefinition-structure.md)
    
  - [How to: Parse a stream from a binary property to read the TZREG structure](how-to-parse-a-stream-from-a-binary-property-to-read-the-tzreg-structure.md)
    
  - [How to: Read time zone properties from an appointment](how-to-read-time-zone-properties-from-an-appointment.md)
    
  - [How to: Specify whether to display a contact's picture in Outlook (Outlook Auxiliary Reference)](how-to-specify-whether-to-display-a-contact-s-picture-in-outlook-outlook-auxilia.md)
    
  - [How to: Use relative time to access free/busy data](how-to-use-relative-time-to-access-free-busy-data.md)
    
The reference for each API lists the constants, type definitions, and interfaces that a developer must implement to use the additional functionality.
  
> [!NOTE]
> Developers must implement these APIs only as documented in this reference. Certain interface members and method parameters are named as placeholders because they are reserved for the internal use of Outlook and are subject to change without notice. 
  

