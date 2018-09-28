---
title: Folders
TOCTitle: Folders
ms:assetid: b72b5705-d77a-4cad-873d-457b9fb6553e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184634(v=office.15)
ms:contentKeyID: 55119856
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Folders

This section provides sample tasks that involve folders. [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) objects represent the folder hierarchy where Microsoft Outlook items are stored. Examples of folders include the Calendar, Mail, and Deleted Items folders. In the Outlook Primary Interop Assembly (PIA), members of the Folder object are exposed as members of the [MAPIFolder](https://msdn.microsoft.com/en-us/library/bb624369\(v=office.15\)) object.

## In this section

  - [Add a Folder to the Folder List](how-to-add-a-folder-to-the-folder-list.md)  
    Uses the [Add(String, Object)](https://msdn.microsoft.com/en-us/library/bb645065\(v=office.15\)) method to add a folder to the Outlook folder list.

  - [Enumerate Folders](how-to-enumerate-folders.md)  
    Enumerates folders by iterating through a collection of folders.

  - [Get a Default Folder and Enumerate Its Subfolders](how-to-get-a-default-folder-and-enumerate-its-subfolders.md)  
    Obtains a default folder in the user’s default store and enumerates its subfolders.

  - [Get a Folder Based on Its Folder Path](how-to-get-a-folder-based-on-its-folder-path.md)  
    Takes a folder path and obtains the associated folder.

  - [Select a Folder and Display Folder Information](how-to-select-a-folder-and-display-folder-information.md)  
    Programmatically displays information about a folder that a user selects from a specified folder list.

  - [Get the Default Message Class of a Folder](how-to-get-the-default-message-class-of-a-folder.md)  
    Uses the [DefaultMessageClass](https://msdn.microsoft.com/en-us/library/bb646541\(v=office.15\)) property to obtain the default message class of a folder.

  - [Access Solution-Specific Data Stored as a Hidden Message in a Folder](how-to-access-solution-specific-data-stored-as-a-hidden-message-in-a-folder.md)  
    Uses the [StorageItem](https://msdn.microsoft.com/en-us/library/bb623436\(v=office.15\)) object to retrieve data that is stored as a hidden message of a specific message class in a folder.

  - [Ensure that Custom Item Properties Are Supported in Folder-Level Queries](how-to-ensure-that-custom-item-properties-are-supported-in-folder-level-queries.md)  
    Shows how to ensure that when you add a custom property to an item type, you also add the property to the folder so that you can query on that custom property at the folder level.

## See also

[Calendar](calendar.md)

[Contacts](contacts.md)

[Mail](mail.md)

## See also



[How Do I... (Outlook 2013 PIA Reference)](how-do-i-outlook-2013-pia-reference.md)

