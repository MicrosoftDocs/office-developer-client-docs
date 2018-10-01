---
title: 'Use Instant Search to Search All Folders and All Stores for a Phrase in the Subject'
TOCTitle: 'Use Instant Search to Search All Folders and All Stores for a Phrase in the Subject'
ms:assetid: d3152bfa-6e7d-4b68-8c7e-e2e155a92b49
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424478(v=office.15)
ms:contentKeyID: 55119923
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Use Instant Search to Search All Folders and All Stores for a Phrase in the Subject

This example uses Instant Search to search all folders and all stores for a phrase in the subject, and then displays the items in an explorer window.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

Instant Search is a feature of Microsoft Outlook that enables you to search by issuing queries that return results based on the content. Once your query has been processed, the results can be returned in a variety of objects, including the [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object, the [Items](https://msdn.microsoft.com/en-us/library/bb645287\(v=office.15\)) collection, and the [Search](https://msdn.microsoft.com/en-us/library/bb612611\(v=office.15\)) object. You can write code that uses Instant Search by using the Advanced Query Syntax (AQS) that is offered by Microsoft Windows Desktop Search. AQS is one of three query languages that Outlook supports. It is powerful, but limited to the [Search(String, OlSearchScope)](https://msdn.microsoft.com/en-us/library/bb610561\(v=office.15\)) method of the [Explorer](https://msdn.microsoft.com/en-us/library/bb623678\(v=office.15\)) object. You cannot use AQS to provide a restriction for Table or item objects. In addition, the results returned by an AQS query can be displayed only in the Outlook user interface. The following table lists the three query languages that Outlook supports; however, this topic will illustrate the use of only AQS.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Query language</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AQS</p></td>
<td><p>AQS is used by Windows Desktop Search and is the query language for the Instant Search feature in Outlook.</p></td>
</tr>
<tr class="even">
<td><p>DASL</p></td>
<td><p>DAV Search and Locating (DASL) query language is based on the Microsoft Exchange implementation of DASL in Outlook. DASL can be used to return results in the Table object.</p></td>
</tr>
<tr class="odd">
<td><p>Jet</p></td>
<td><p>Jet query language provides a simple query language for Outlook, and is based on the Microsoft Jet Expression Service. Jet is used to create filter strings for the Restrict methods of the Items collection and the Table object.</p></td>
</tr>
</tbody>
</table>


In the following code example, DemoInstantSearch gets all mail folders in all stores where indexing is enabled by using the [IsInstantSearchEnabled](https://msdn.microsoft.com/en-us/library/bb609793\(v=office.15\)) property of the [Store](https://msdn.microsoft.com/en-us/library/bb609139\(v=office.15\)) object. It then uses the Search method of the Explorer object to filter for all items that contain the exact phrase “Office 2007” in the subject and that have been received in the last month. The results of the search are finally displayed in a separate explorer window.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void DemoInstantSearch()
{
    if (Application.Session.DefaultStore.IsInstantSearchEnabled)
    {
        Outlook.Explorer explorer = Application.Explorers.Add(
            Application.Session.GetDefaultFolder(
            Outlook.OlDefaultFolders.olFolderInbox)
            as Outlook.Folder,
            Outlook.OlFolderDisplayMode.olFolderDisplayNormal);
        string filter = "subject:" +
            "\"" + "Office 2007" + "\"" +
            " received:(last month)";
        explorer.Search(filter,
            Outlook.OlSearchScope.olSearchScopeAllFolders);
        explorer.Display();
    }
}
```

## See also



[Search and Filter](search-and-filter.md)

