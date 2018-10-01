---
title: 'Use SetColumns to Efficiently Enumerate Items in a Folder'
TOCTitle: 'Use SetColumns to Efficiently Enumerate Items in a Folder'
ms:assetid: cd7c7758-8a9c-4f1c-a49c-9305d75be341
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184641(v=office.15)
ms:contentKeyID: 55119921
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Use SetColumns to Efficiently Enumerate Items in a Folder

This example shows how to improve the performance of enumerating the [Items](https://msdn.microsoft.com/en-us/library/bb645287\(v=office.15\)) collection by using the [SetColumns(String)](https://msdn.microsoft.com/en-us/library/bb610268\(v=office.15\)) method to cache certain properties of each item in the collection.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

To enumerate items in a collection, use the SetColumns method to cache properties on the Items collection. SetColumns takes an argument that is a comma-delimited string that represents property names. Once all items in the collection have been enumerated, call the [ResetColumns()](https://msdn.microsoft.com/en-us/library/bb624355\(v=office.15\)) method to clear the property cache.

In the following code example, EnumerateContactsWithSetColumns uses the SetColumns method to cache the [FileAs](https://msdn.microsoft.com/en-us/library/bb647792\(v=office.15\)), [CompanyName](https://msdn.microsoft.com/en-us/library/bb610212\(v=office.15\)), and [JobTitle](https://msdn.microsoft.com/en-us/library/bb609294\(v=office.15\)) properties of items in the Contacts folder. Note that you must test for empty strings or a null reference in the restriction.

Note that an Outlook folder can possibly contain items of different types. This code sample makes use of the OutlookItem helper class, defined in [Create a Helper Class to Access Common Outlook Item Members](how-to-create-a-helper-class-to-access-common-outlook-item-members.md), to conveniently call the OutlookItem.Class property to verify the message class of each item in the filtered subset of items in the folder, before assuming the item is a contact item.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void EnumerateContactsWithSetColumns()
{
    // Obtain Contacts folder
    Outlook.Folder folder =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderContacts)
        as Outlook.Folder;
    string filter = "Not([CompanyName] Is Null)" +
        " AND Not([JobTitle] Is Null)";
    Outlook.Items items = folder.Items.Restrict(filter);
    items.SetColumns("FileAs, CompanyName, JobTitle");
    for (int i = 1; i <= items.Count; i++)
    {
        // Create an instance of OutlookItem
        OutlookItem myItem = new OutlookItem(items[i]);
        if (myItem.Class == Outlook.OlObjectClass.olContact)
        {
            // Use InnerObject to return ContactItem
            Outlook.ContactItem contact =
                myItem.InnerObject as Outlook.ContactItem;
            StringBuilder sb = new StringBuilder();
            sb.AppendLine(contact.FileAs);
            sb.AppendLine(contact.CompanyName);
            sb.AppendLine(contact.JobTitle);
            sb.AppendLine();
            Debug.WriteLine(sb.ToString());
        }
    }
    items.ResetColumns();
}
```

## See also



[Search and Filter](search-and-filter.md)

