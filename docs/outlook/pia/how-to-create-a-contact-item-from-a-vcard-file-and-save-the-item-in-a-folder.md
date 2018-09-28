---
title: 'Create a Contact Item from a vCard file and Save the Item in a Folder'
TOCTitle: 'Create a Contact Item from a vCard file and Save the Item in a Folder'
ms:assetid: b207b584-ffcf-4ac5-ab1f-4f91d43000e1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb646856(v=office.15)
ms:contentKeyID: 55119826
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Create a Contact Item from a vCard file and Save the Item in a Folder

This example imports all the vCard files in a file system folder and saves the contacts into the folder specified by the targetFolder parameter.

## Example

This example uses the [OpenSharedItem](https://msdn.microsoft.com/en-us/library/bb645399\(v=office.15\)) method. The OpenSharedItem method opens messages stored as Outlook message format (.msg) files, iCalendar appointment (.ics) files, or vCard (.vcf) files. Be sure to cast the returned object to the appropriate item type and call the corresponding Save method to persist the item. By default, the item returned by OpenSharedItem is saved in the default folder for the specific item type. You can use the corresponding Move method to move the item to a different folder.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The Imports or using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

```vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```vb
Private Sub ImportContacts( _
    ByVal path As String, ByVal targetFolder As Outlook.Folder)
    Dim contact As Outlook.ContactItem
    Dim moveContact As Outlook.ContactItem
    If (Directory.Exists(path)) Then
        Dim files As String() = Directory.GetFiles(path, "*.vcf")
        For Each file As String In files
            contact = CType(Application.Session.OpenSharedItem(file), _
                Outlook.ContactItem)
            If (targetFolder Is _
                CType(Application.Session.GetDefaultFolder( _
                    Outlook.OlDefaultFolders.olFolderContacts) _
                    , Outlook.Folder)) Then
                contact.Save()
            Else
                moveContact = CType(contact.Move(targetFolder), _
                    Outlook.ContactItem)
                moveContact.Save()
            End If
        Next
    End If
End Sub
```

```csharp
private void ImportContacts(string path, Outlook.Folder targetFolder)
{
    Outlook.ContactItem contact;
    Outlook.ContactItem moveContact;
    if (Directory.Exists(path))
    {
        string[] files = Directory.GetFiles(path, "*.vcf");
        foreach (string file in files)
        {
            contact = Application.Session.OpenSharedItem(file)
                as Outlook.ContactItem;
            if (targetFolder ==
                Application.Session.GetDefaultFolder(
                Outlook.OlDefaultFolders.olFolderContacts)
                as Outlook.Folder)
            {
                contact.Save();
            }
            else
            {
                moveContact = contact.Move(targetFolder)
                    as Outlook.ContactItem;
                moveContact.Save();
            }
        }
    }
}
```

## See also



[Contacts](contacts.md)

