---
title: 'Filter and Display Inbox Items Modified in the Last Month'
TOCTitle: 'Filter and Display Inbox Items Modified in the Last Month'
ms:assetid: ef6004dc-0b5a-4d1f-8937-1384d1dfc1ca
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424482(v=office.15)
ms:contentKeyID: 55119886
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Filter and Display Inbox Items Modified in the Last Month

This example shows how to filter and display Inbox items that were modified in the last month.

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


DAV Searching and Locating (DASL) query language is based on the Microsoft Exchange implementation of DASL in Outlook. It can be used to return property-based results for item-level searches in folder data, such as that represented by a [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object. DASL filters support string comparisons, including equivalence, prefix, phrase, and substring matching, by using the equal (=) operator. You can use DASL queries to perform date-time comparison and filtering.

Because DASL queries always perform DateTime comparisons in Coordinated Universal Time (UTC), you must convert the local time value to UTC if you want the query to operate correctly. You must also convert the DateTime value to a string representation because DASL filters support string comparisons. You can make the DateTime conversion in two ways: by using the [LocalTimeToUTC(Object)](https://msdn.microsoft.com/en-us/library/bb645832\(v=office.15\)) method of the [Row](https://msdn.microsoft.com/en-us/library/bb610126\(v=office.15\)) object, or by using Outlook DateTime macros to make the conversion.

The following line of code shows how to use the LocalTimeToUTC method to convert the value of the LastModificationTime property (which is a default column in all Item objects) to UTC.

```csharp
DateTime modified = nextRow.LocalTimeUTC(“LastModificationTime”);
```

The following table lists the DateTime macros you can use to return filtered strings that compare the value of a given DateTime property with a specified relative date or date range in UTC. The SchemaName property value represents any valid DateTime property referenced by namespace.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Macro</p></th>
<th><p>Syntax</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>today</p></td>
<td><p>%today(“SchemaName”)%</p></td>
<td><p>Restricts for items with a SchemaName property value equal to today.</p></td>
</tr>
<tr class="even">
<td><p>tomorrow</p></td>
<td><p>%tomorrow(“SchemaName”)%</p></td>
<td><p>Restricts for items with a SchemaName property value equal to tomorrow.</p></td>
</tr>
<tr class="odd">
<td><p>yesterday</p></td>
<td><p>%yesterday(“SchemaName”)%</p></td>
<td><p>Restricts for items with a SchemaName property value equal to yesterday.</p></td>
</tr>
<tr class="even">
<td><p>next7days</p></td>
<td><p>%next7days(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to the next seven days.</p></td>
</tr>
<tr class="odd">
<td><p>last7days</p></td>
<td><p>%last7days(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to the last seven days.</p></td>
</tr>
<tr class="even">
<td><p>nextweek</p></td>
<td><p>%nextweek(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to next week.</p></td>
</tr>
<tr class="odd">
<td><p>thisweek</p></td>
<td><p>%thisweek(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to this week.</p></td>
</tr>
<tr class="even">
<td><p>lastweek</p></td>
<td><p>%lastweek(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to last week.</p></td>
</tr>
<tr class="odd">
<td><p>nextmonth</p></td>
<td><p>%nextmonth(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to next month.</p></td>
</tr>
<tr class="even">
<td><p>thismonth</p></td>
<td><p>%thismonth(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to this month.</p></td>
</tr>
<tr class="odd">
<td><p>lastmonth</p></td>
<td><p>%lastmonth(“SchemaName”)%</p></td>
<td><p>Restricts for items with SchemaName property values in a range equivalent to last month.</p></td>
</tr>
</tbody>
</table>


In the following example, DemoDASLDateMacro creates a DASL query that uses the lastmonthDateTime macro to filter for items in the user’s Inbox that were modified in the last month. It then creates a Table object with that filter, and enumerates and displays the rows in the restricted Table object.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void DemoDASLDateMacro()
{
    string filter = "@SQL=" + "%lastmonth(" + "\"" +
        "DAV:getlastmodified" + "\"" + ")%";
    Outlook.Table table = Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox).GetTable(
        filter, Outlook.OlTableContents.olUserItems);
    while (!table.EndOfTable)
    {
        Outlook.Row row = table.GetNextRow();
        Debug.WriteLine(row["Subject"]);
    }
}
```

## See also



[Search and Filter](search-and-filter.md)

