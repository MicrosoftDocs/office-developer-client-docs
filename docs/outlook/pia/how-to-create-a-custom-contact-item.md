---
title: 'Create a Custom Contact Item'
TOCTitle: 'Create a Custom Contact Item'
ms:assetid: 24b2a104-a0a7-469b-9676-a07cab613f59
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184596(v=office.15)
ms:contentKeyID: 55119831
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Create a Custom Contact Item

This example shows how to create a custom contact item and set both predefined and user-defined properties.

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


A [ContactItem](https://msdn.microsoft.com/en-us/library/bb644956\(v=office.15\)) object represents a contact in the Contacts folder, and has more than 100 built-in properties such as [FirstName](https://msdn.microsoft.com/en-us/library/bb652965\(v=office.15\)) and [LastName](https://msdn.microsoft.com/en-us/library/bb609750\(v=office.15\)). Sometimes, the built-in properties are not sufficient and you need to add custom properties, which you can do by using the [UserProperties](https://msdn.microsoft.com/en-us/library/bb611428\(v=office.15\)) collection.

In the following code example, CreateCustomItem creates a custom ContactItem object, names it "Shoe Store", and calls the [Add(String, Object)](https://msdn.microsoft.com/en-us/library/bb645065\(v=office.15\)) method to add it to a folder named "Shoe Store". CreateCustomItem first gets the "Shoe Store" folder by using the [GetDefaultFolder(OlDefaultFolders)](https://msdn.microsoft.com/en-us/library/bb646473\(v=office.15\)) method. The "Shoe Store" folder is a subfolder of the default Contacts folder. CreateCustomItem then sets the FirstName and LastName properties, and creates a user-defined property ("Shoe Size") by using the UserProperties collection.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void CreateCustomItem()
{
    Outlook.Folder folder =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderContacts).Folders[
        "Shoe Store"] as Outlook.Folder;
    Outlook.ContactItem contact =
        folder.Items.Add(
        "IPM.Contact.Shoe Store") as Outlook.ContactItem;
    contact.FirstName = "Michael";
    contact.LastName = "Affronti";
    contact.UserProperties["Shoe Size"].Value = "9";
    contact.Save();
}
```

## See also



[Contacts](contacts.md)

