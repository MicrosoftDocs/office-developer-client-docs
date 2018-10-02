---
title: Use arrays to efficiently enumerate items in a folder
TOCTitle: Use arrays to efficiently enumerate items in a folder
ms:assetid: 05a73225-ad0d-4d52-90b6-448d220348df
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184588(v=office.15)
ms:contentKeyID: 55119885
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Use arrays to efficiently enumerate items in a folder

This example shows how to efficiently enumerate items in a [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) object by using the [GetArray(Int32)](https://msdn.microsoft.com/en-us/library/bb608928\(v=office.15\)) method.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

In the following code example, DemoGetArrayForTable gets a [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object from a **Folder** object by using the [GetTable(Object, Object)](https://msdn.microsoft.com/en-us/library/bb612592\(v=office.15\)) method. DemoGetArrayForTable then uses the **GetArray** method to return an [Array](http://msdn.microsoft.com/en-us/library/system.array.aspx) object that contains elements for every row in the table. The returned **Array** object is a two-dimensional array that represents a set of row and column values from the **Table**. The array is zero-based, instead of one-based as is the case with Outlook collections. Once the **Array** object is obtained, the code uses a for loop to enumerate through the table.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void DemoGetArrayForTable()
{
    // Obtain Inbox
    Outlook.Folder folder =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    Outlook.Table table =
        folder.GetTable("", Outlook.OlTableContents.olUserItems);
    Array tableArray = table.GetArray(table.GetRowCount()) as Array;
    for (int i = 0; i <= tableArray.GetUpperBound(0); i++)
    {
        for (int j = 0; j <= tableArray.GetUpperBound(1); j++)
        {
            Debug.WriteLine(tableArray.GetValue(i, j));
        }
    }
}
```

## See also

- [Search and filter](search-and-filter.md)

