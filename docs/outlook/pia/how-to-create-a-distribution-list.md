---
title: 'How to: Create a Distribution List'
TOCTitle: 'How to: Create a Distribution List'
ms:assetid: c1fdbf3d-9669-4721-aabf-e8a332b82e0e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184637(v=office.15)
ms:contentKeyID: 55119841
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Create a Distribution List

This example shows how to create a distribution list and display it to the user.

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


In the following code example, CreateDistributionList creates a distribution list by calling the [CreateItem(OlItemType)](https://msdn.microsoft.com/en-us/library/bb610587\(v=office.15\)) method to create a [DistListItem](https://msdn.microsoft.com/en-us/library/bb645382\(v=office.15\)) object. Next it creates a [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object, and calls the [GetTable(Object, Object)](https://msdn.microsoft.com/en-us/library/bb612189\(v=office.15\)) method to find all contacts in the default Contacts folder for which the [Subject](https://msdn.microsoft.com/en-us/library/bb624088\(v=office.15\)) property value is “Top Customer” and the [Email1Address](https://msdn.microsoft.com/en-us/library/bb609902\(v=office.15\)) property value is not empty. Once all contacts are identified, the Email1Address name is added as a column to the Table. CreateDistributionList then creates a [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) object by using the [CreateRecipient(String)](https://msdn.microsoft.com/en-us/library/bb609962\(v=office.15\)) method from the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object. CreateDistributionList finally displays the “Top Customers” distribution list to the user.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>C# note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>You must pass a resolved Recipient object as a parameter to the <a href="https://msdn.microsoft.com/en-us/library/bb612290(v=office.15)">AddMember(Recipient)</a> method of the <a href="https://msdn.microsoft.com/en-us/library/bb645382(v=office.15)">DistListItem</a> object. To resolve a Recipient object, use the <a href="https://msdn.microsoft.com/en-us/library/bb624165(v=office.15)">Resolve()</a> method.</p></td>
</tr>
</tbody>
</table>


If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void CreateDistributionList()
{
    Outlook.DistListItem distList = Application.CreateItem(
        Outlook.OlItemType.olDistributionListItem)
        as Outlook.DistListItem;
    distList.Subject = "Top Customers";
    //Find top customer category in Contacts folder
    string filter = "[Categories] = 'Top Customer'"
        + " AND [Email1Address] <> ''";
    Outlook.Table table =
        Application.Session.GetDefaultFolder
        (Outlook.OlDefaultFolders.olFolderContacts).
        GetTable(filter, Outlook.OlTableContents.olUserItems);
    table.Columns.Add("Email1Address");
    while (!table.EndOfTable)
    {
        Outlook.Row nextRow = table.GetNextRow();
        Outlook.Recipient recip =
            Application.Session.CreateRecipient(
            nextRow["Email1Address"].ToString());
        //Resolve the Recipient before calling AddMember
        recip.Resolve();
        distList.AddMember(recip);
    }
    distList.Display(false);
}
```

## See also



[Exchange Users](exchange-users.md)

