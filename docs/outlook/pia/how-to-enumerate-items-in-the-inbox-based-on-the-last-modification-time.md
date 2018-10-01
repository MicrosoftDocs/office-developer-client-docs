---
title: 'Enumerate Items in the Inbox Based on the Last Modification Time'
TOCTitle: 'Enumerate Items in the Inbox Based on the Last Modification Time'
ms:assetid: 93a25143-def6-4832-bac2-3744558c2736
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184626(v=office.15)
ms:contentKeyID: 55119920
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Enumerate Items in the Inbox Based on the Last Modification Time

This example shows how to enumerate items in the Inbox folder based on the last modification time.

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


The [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object represents a set of items from a [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) or [Search](https://msdn.microsoft.com/en-us/library/bb612611\(v=office.15\)) object. To obtain a Table, call the [GetTable(Object, Object)](https://msdn.microsoft.com/en-us/library/bb612592\(v=office.15\)) method on a Folder or Search object. Each item in the returned Table contains only a default subset of the item’s properties. Each [Row](https://msdn.microsoft.com/en-us/library/bb610126\(v=office.15\)) object can be regarded as an item in the folder, and each [Column](https://msdn.microsoft.com/en-us/library/bb609646\(v=office.15\)) object as a property of an item. Removing, adding, or changing rows is not supported in the Table. To enumerate items in a Table, first use the [EndOfTable](https://msdn.microsoft.com/en-us/library/bb647715\(v=office.15\)) property to see whether your current position is at the end of the table. If EndOfTable returns false, use the [GetNextRow()](https://msdn.microsoft.com/en-us/library/bb609740\(v=office.15\)) method to return a Row, which contains a default number of Column objects. You continue iterating in a forward manner through the Table by calling GetNextRow until EndOfTable returns true.

In the following code example, DemoTableForInbox obtains a Table object for the Inbox folder, sorts the Table object by using the LastModificationTime property and [Sort(String, Object)](https://msdn.microsoft.com/en-us/library/bb652667\(v=office.15\)) method, and iterates through the table to write the subject of each item to the trace listeners of the [Listeners](http://msdn.microsoft.com/en-us/library/system.diagnostics.debug.listeners.aspx) collection.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void DemoTableForInbox()
{
    //Obtain Inbox
    Outlook.Folder folder =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    //Obtain Table using defaults
    Outlook.Table table =
        folder.GetTable(Type.Missing, Type.Missing);
    table.Sort("LastModificationTime",
        Outlook.OlSortOrder.olDescending);
    while (!table.EndOfTable)
    {
        Outlook.Row nextRow = table.GetNextRow();
        Debug.WriteLine(nextRow["Subject"]);
    }
}
```

## See also



[Search and Filter](search-and-filter.md)

