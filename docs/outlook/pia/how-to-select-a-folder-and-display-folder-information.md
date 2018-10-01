﻿---
title: Select a folder and display folder information
TOCTitle: Select a folder and display folder information
ms:assetid: 737b19bc-1efd-4ddb-86d0-72b3ab8eaf8c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184616(v=office.15)
ms:contentKeyID: 55119859
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Select a folder and display folder information

This example shows how to programmatically display information about a folder that a user selects from a specified folder list.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

In the following code example, ShowFolderInfo uses the [PickFolder()](https://msdn.microsoft.com/en-us/library/bb623484\(v=office.15\)) method of the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object to display a **Select Folder** dialog box to the user, and waits for the user to select a folder. Once the user selects a folder, its [EntryID](https://msdn.microsoft.com/en-us/library/bb646192\(v=office.15\)), [StoreID](https://msdn.microsoft.com/en-us/library/bb612609\(v=office.15\)), [UnReadItemCount](https://msdn.microsoft.com/en-us/library/bb610138\(v=office.15\)), [DefaultMessageClass](https://msdn.microsoft.com/en-us/library/bb646541\(v=office.15\)), [CurrentView](https://msdn.microsoft.com/en-us/library/bb612411\(v=office.15\)), [Name](https://msdn.microsoft.com/en-us/library/bb623727\(v=office.15\)), and [FolderPath](https://msdn.microsoft.com/en-us/library/bb647409\(v=office.15\)) properties are displayed. The example then calls the [GetFolderFromID](https://msdn.microsoft.com/en-us/library/bb647784\(v=office.15\)) method to create a new [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) object and display the folder.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void ShowFolderInfo()
{
    Outlook.Folder folder =
        Application.Session.PickFolder()
        as Outlook.Folder;
    if (folder != null)
    {
        StringBuilder sb = new StringBuilder();
        sb.AppendLine("Folder EntryID:");
        sb.AppendLine(folder.EntryID);
        sb.AppendLine();
        sb.AppendLine("Folder StoreID:");
        sb.AppendLine(folder.StoreID);
        sb.AppendLine();
        sb.AppendLine("Unread Item Count: "
            + folder.UnReadItemCount);
        sb.AppendLine("Default MessageClass: "
            + folder.DefaultMessageClass);
        sb.AppendLine("Current View: "
            + folder.CurrentView.Name);
        sb.AppendLine("Folder Path: "
            + folder.FolderPath);
        MessageBox.Show(sb.ToString(),
            "Folder Information",
            MessageBoxButtons.OK,
            MessageBoxIcon.Information);
        Outlook.Folder folderFromID =
            Application.Session.GetFolderFromID(
            folder.EntryID, folder.StoreID)
            as Outlook.Folder;
        folderFromID.Display();
    }
}
```

## See also

- [Folders](folders.md)

