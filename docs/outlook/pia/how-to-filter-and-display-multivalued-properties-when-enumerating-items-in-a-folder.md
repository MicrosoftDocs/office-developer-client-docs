---
title: Filter and display multivalued properties when enumerating items in a folder
TOCTitle: Filter and display multivalued properties when enumerating items in a folder
ms:assetid: 62dd2120-5c85-44b3-89ec-c4ca85aa2964
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184613(v=office.15)
ms:contentKeyID: 55119887
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Filter and display multivalued properties when enumerating items in a folder

This example shows how to filter and display multivalued properties while enumerating items in a folder.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

The [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object represents a set of item data from a [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) or [Search](https://msdn.microsoft.com/en-us/library/bb612611\(v=office.15\)) object. When a binary, date, or multivalued property is first added to a **Table** object, the way the property is referenced affects its type and format. Because built-in name references sometimes return a different column value than a namespace reference, you should determine whether the property is referenced by its explicit built-in name (if it has one), or by namespace (regardless of the existence of an explicit built-in name). The following table shows the difference in the property value representation (in terms of type and format) per original property type.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Type</p></th>
<th><p>Return type if the specified property uses a built-in name</p></th>
<th><p>Return type if the specified property uses a namespace</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Binary <b>(PT_BINARY)</b></p></td>
<td><p>String</p></td>
<td><p>Byte array</p></td>
</tr>
<tr class="even">
<td><p>Date <b>(PT_SYSTIME)</b></p></td>
<td><p>Local <b>DateTime</b></p></td>
<td><p>UTC <b>DateTime</b></p></td>
</tr>
<tr class="odd">
<td><p>Multivalued (also known as keyword type) such as <b>Categories</b> property <b>(PT_MV_STRING8)</b></p></td>
<td><p>String that contains comma-separated values</p></td>
<td><p>One-dimensional array that contains one element for each keyword</p></td>
</tr>
</tbody>
</table>


The following code example illustrates how to add a MAPI string namespace property to the **Table** object and how multivalued properties affect the values returned in a [Column](https://msdn.microsoft.com/en-us/library/bb609646\(v=office.15\)) object. The TableMultiValuedProperties procedure filters the **Table** object for rows where the [Categories](https://msdn.microsoft.com/en-us/library/bb646607\(v=office.15\)) property is not a null reference. The **Categories** property is represented by a property that uses the MAPI string namespace. A DAV Searching and Locating (DASL) filter is constructed for items that have categories (the actual filter returns categories that do not have a null reference). A **Categories** column is then added to the **Table** object by concatenating the type specifier, 0000001f, with the categoriesProperty constant. Finally, the **Column** object that represents the **Categories** property contains a one-dimensional string array where each element of the array represents a category assigned to the item. Both the item’s **Categories** and **Subject** properties are written to the trace listeners of the [Listeners](http://msdn.microsoft.com/en-us/library/system.diagnostics.debug.listeners.aspx) collection.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void TableMultiValuedProperties()
{
    const string categoriesProperty =
        "http://schemas.microsoft.com/mapi/string/"
        + "{00020329-0000-0000-C000-000000000046}/Keywords";
    // Inbox
    Outlook.Folder folder =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    // Call GetTable with filter for categories
    string filter = "@SQL="
        + "Not(" + "\"" + categoriesProperty
        + "\"" + " Is Null)";
    Outlook.Table table =
        folder.GetTable(filter,
        Outlook.OlTableContents.olUserItems);
    // Add categories column and append type specifier
    table.Columns.Add(categoriesProperty + "/0000001F");
    while (!table.EndOfTable)
    {
        Outlook.Row nextRow = table.GetNextRow();
        string[] categories =
            (string[])nextRow[categoriesProperty + "/0000001F"];
        Debug.WriteLine("Subject: " + nextRow["Subject"]);
        Debug.Write("Categories: ");
        foreach (string category in categories)
        {
            Debug.Write("\t" + category);
        }
        Debug.WriteLine("\n");
    }
}
```

## See also

- [Search and filter](search-and-filter.md)

