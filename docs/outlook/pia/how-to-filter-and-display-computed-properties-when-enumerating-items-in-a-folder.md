---
title: Filter and display computed properties when enumerating items in a folder
TOCTitle: Filter and display computed properties when enumerating items in a folder
ms:assetid: b068e625-ff12-444d-a30d-51a3acba3043
ms:mtpsurl: https://msdn.microsoft.com/library/Ff184632(v=office.15)
ms:contentKeyID: 55119922
ms.date: 07/24/2014
mtps_version: v=office.15
localization_priority: Normal
---

# Filter and display computed properties when enumerating items in a folder

This example shows how to filter and display computed properties when enumerating items in a folder.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).


The [Table](https://msdn.microsoft.com/library/bb652856\(v=office.15\)) object represents a set of item data from a [Folder](https://msdn.microsoft.com/library/bb645774\(v=office.15\)) or [Search](https://msdn.microsoft.com/library/bb612611\(v=office.15\)) object. The [Row](https://msdn.microsoft.com/library/bb610126\(v=office.15\)) object represents rows of data in a **Table**. The [Columns](https://msdn.microsoft.com/library/bb646214\(v=office.15\)) object represents properties of the **Table**. You can add certain properties to the **Table** object by using the [Add(String)](https://msdn.microsoft.com/library/bb652865\(v=office.15\)) method of the **Columns** object. You can filter certain properties by using the [Restrict(String)](https://msdn.microsoft.com/library/bb612178\(v=office.15\)) method of the **Table** object. However, some properties cannot be added to the **Table** object by using **Columns.Add**, nor can they be filtered by using the **Restrict** method. The following table describes whether properties are supported for the **Table** object when you use the **Columns.Add** or **Restrict** method.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Property</p></th>
<th><p>For Columns.Add</p></th>
<th><p>For Restrict</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Binary properties such as <b>EntryID</b>.</p></td>
<td><p>Supported via built-in or namespace property.</p></td>
<td><p>Not supported. Outlook will raise an error.</p></td>
</tr>
<tr class="even">
<td><p>Body properties, including <b>Body</b> and <b>HTMLBody</b>, and namespace representation of those properties, including <b>PR_RTF_COMPRESSED</b>.</p></td>
<td><p>The <b>Body</b> property is supported with a condition that only the first 255 bytes of the value are stored in a <b>Table</b> object. Other properties that represent the body content in HTML or RTF are not supported. Because only the first 255 bytes of <b>Body</b> are returned, if you want to obtain the full body content of an item in text or HTML, use the item’s <b>EntryID</b> in the <a href="https://msdn.microsoft.com/library/bb644121(v=office.15)">GetItemFromID(String, Object)</a> method to obtain the item object. Then retrieve the full value of <b>Body</b> through the item object.</p></td>
<td><p>Only the <b>Body</b> property represented in text is supported in a filter. This means that the property must be referenced in a DAV Searching and Locating (DASL) filter as <em>urn:schemas:http-mail:textdescription</em>, and you cannot filter on any HTML tags in the body. To improve performance, use context indexer keywords in the filter to match strings in the body.</p></td>
</tr>
<tr class="odd">
<td><p>Computer properties, such as <b>AutoResolvedWinner</b> and <b>BodyFormat</b>.</p></td>
<td><p>Not supported.</p></td>
<td><p>Not supported.</p></td>
</tr>
<tr class="even">
<td><p>Multivalued properties, such as <b>Categories</b>, <b>Children</b>, <b>Companies</b>, and <b>VotingOptions</b>.</p></td>
<td><p>Supported.</p></td>
<td><p>Supported, provided that you can create a DASL query by using the namespace representation.</p></td>
</tr>
<tr class="odd">
<td><p>Properties that return an object, such as <b>Attachments</b>, <b>Parent</b>, <b>Recipients</b>, <b>RecurrencePattern</b>, and <b>UserProperties</b>.</p></td>
<td><p>Not supported.</p></td>
<td><p>Not supported.</p></td>
</tr>
</tbody>
</table>


The following table lists known invalid properties that cannot be added to the **Table** object by using **Columns.Add**. If you attempt to add a property from this list, Outlook will raise an error.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>AutoResolvedWinner</p></td>
<td><p>BodyFormat</p></td>
<td><p>Class</p></td>
</tr>
<tr class="even">
<td><p>Companies</p></td>
<td><p>ContactNames</p></td>
<td><p>DLName</p></td>
</tr>
<tr class="odd">
<td><p>DownloadState</p></td>
<td><p>FlagIcon</p></td>
<td><p>HtmlBody</p></td>
</tr>
<tr class="even">
<td><p>InternetCodePage</p></td>
<td><p>IsConflict</p></td>
<td><p>IsMarkedAsTask</p></td>
</tr>
<tr class="odd">
<td><p>MeetingWorkspaceURL</p></td>
<td><p>MemberCount</p></td>
<td><p>Permission</p></td>
</tr>
<tr class="even">
<td><p>PermissionService</p></td>
<td><p>RecurrenceState</p></td>
<td><p>ResponseState</p></td>
</tr>
<tr class="odd">
<td><p>Saved</p></td>
<td><p>Sent</p></td>
<td><p>Submitted</p></td>
</tr>
<tr class="even">
<td><p>TaskSubject</p></td>
<td><p>Unread</p></td>
<td><p>VotingOptions</p></td>
</tr>
</tbody>
</table>


Although some computed properties cannot be added to the column set for a table, the following code example works around this limitation. GetToDoItems uses a DASL query to restrict the items that appear in the **Table**. If the computed property has a namespace representation, the namespace representation is used to create a DASL query that restricts the **Table** object to return rows for a specified value of the computed property. GetToDoItems gets items in the Inbox where the value of the [IsMarkedAsTask](https://msdn.microsoft.com/library/bb623631\(v=office.15\)) property is equal to **true**, and then assigns values to certain task properties such as [TaskSubject](https://msdn.microsoft.com/library/bb643880\(v=office.15\)), [TaskDueDate](https://msdn.microsoft.com/library/bb623035\(v=office.15\)), [TaskStartDate](https://msdn.microsoft.com/library/bb610832\(v=office.15\)), and [TaskCompletedDate](https://msdn.microsoft.com/library/bb624055\(v=office.15\)). Finally, those properties are written to the trace listeners of the [Listeners](https://msdn.microsoft.com/library/system.diagnostics.debug.listeners.aspx) collection.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void GetToDoItems()
{
    // Obtain Inbox
    Outlook.Folder folder =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    // DASL filter for IsMarkedAsTask
    string filter = "@SQL=" + "\"" +
        "http://schemas.microsoft.com/mapi/proptag/0x0E2B0003"
        + "\"" + " = 1";
    Outlook.Table table =
        folder.GetTable(filter,
        Outlook.OlTableContents.olUserItems);
    table.Columns.Add("TaskStartDate");
    table.Columns.Add("TaskDueDate");
    table.Columns.Add("TaskCompletedDate");
    // Use GUID/ID to represent TaskSubject
    table.Columns.Add(
        "http://schemas.microsoft.com/mapi/id/" +
        "{00062008-0000-0000-C000-000000000046}/85A4001E");
    while (!table.EndOfTable)
    {
        Outlook.Row nextRow = table.GetNextRow();
        StringBuilder sb = new StringBuilder();
        sb.AppendLine("Task Subject: " + nextRow[9]);
        sb.AppendLine("Start Date: "
            + nextRow["TaskStartDate"]);
        sb.AppendLine("Due Date: "
            + nextRow["TaskDueDate"]);
        sb.AppendLine("Completed Date: "
            + nextRow["TaskCompletedDate"]);
        sb.AppendLine();
        Debug.WriteLine(sb.ToString());
    }
}
```

## See also

- [Search and filter](search-and-filter.md)

