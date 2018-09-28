---
title: 'Add a Folder to the Folder List'
TOCTitle: 'Add a Folder to the Folder List'
ms:assetid: f636a190-d966-4421-9977-0ead2bff5eee
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184655(v=office.15)
ms:contentKeyID: 55119850
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Add a Folder to the Folder List

This example shows how to use the [Add(String, Object)](https://msdn.microsoft.com/en-us/library/bb645065\(v=office.15\)) method to add a folder to the Outlook folder list.

## Example

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>The following code example is an excerpt from <em>Programming Applications for Microsoft Office Outlook 2007</em>, from <a href="http://www.microsoft.com/learning/books/default.mspx">Microsoft Press</a> (ISBN 9780735622494, copyright Microsoft Press 2007, all rights reserved).</p>
<p><a href="http://www.amazon.com/gp/product/0735622493?ie=utf8%26tag=msmsdn-20%26linkcode=as2%26camp=1789%26creative=9325%26creativeasin=0735622493">Buy this book</a></p>
<p><a href="https://msdn.microsoft.com/en-us/library/cc513844(v=office.15)">Sample chapters</a></p></td>
</tr>
</tbody>
</table>


In the following code example, AddMyNewFolder calls the Add method of the [Folders](https://msdn.microsoft.com/en-us/library/bb612071\(v=office.15\)) collection to add a [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) object that represents a folder called “My New Folder” to the **Inbox** in the Outlook folder list. “My New Folder” is then displayed.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void AddMyNewFolder()
{
    Outlook.Folder folder =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    Outlook.Folders folders = folder.Folders;
    try
    {
        Outlook.Folder newFolder = folders.Add(
            "My New Folder", Type.Missing)
            as Outlook.Folder;
        newFolder.Display();
    }
    catch
    {
        MessageBox.Show(
            "Could not add 'My New Folder'",
            "Add Folder",
            MessageBoxButtons.OK,
            MessageBoxIcon.Error);
    }
}
```

## See also



[Folders](folders.md)

