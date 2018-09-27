---
title: 'How to: Get Information About Stores in a Profile'
TOCTitle: 'How to: Get Information About Stores in a Profile'
ms:assetid: e88222d2-e1b7-4393-aac4-5ce9d24d5d5b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184648(v=office.15)
ms:contentKeyID: 55119893
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Get Information About Stores in a Profile

This example shows how to get and enumerate stores in a profile.

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


You can use the [Stores](https://msdn.microsoft.com/en-us/library/bb622944\(v=office.15\)) collection to enumerate the stores for a given profile. The Stores collection provides members that expose information about each [Store](https://msdn.microsoft.com/en-us/library/bb609139\(v=office.15\)) object, such as when a Store object has been added or when a Store object is about to be removed in the current profile. In the following code example, EnumerateStores gets the Stores object that represents stores in the current profile, and enumerates the stores. EnumerateStores examines each Store object in the Stores collection. If the [IsDataFileStore](https://msdn.microsoft.com/en-us/library/bb624116\(v=office.15\)) property returns true, indicating that it is a .pst or .ost store, the [DisplayName](https://msdn.microsoft.com/en-us/library/bb612209\(v=office.15\)) and [FilePath](https://msdn.microsoft.com/en-us/library/bb646113\(v=office.15\)) properties are written to the trace listeners in the [Listeners](http://msdn.microsoft.com/en-us/library/system.diagnostics.debug.listeners.aspx) collection.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void EnumerateStores()
{
    Outlook.Stores stores = Application.Session.Stores;
    foreach (Outlook.Store store in stores)
    {
        if (store.IsDataFileStore == true)
        {
            Debug.WriteLine(String.Format("Store: "
            + store.DisplayName
            + "\n" + "File Path: "
            + store.FilePath + "\n"));
        }
    }
}
```

## See also

#### Other resources

[Stores](stores.md)

