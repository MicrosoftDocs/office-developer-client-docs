---
title: 'Add Fields to a View'
TOCTitle: 'Add Fields to a View'
ms:assetid: ea371f27-ea65-47ef-ae44-ef843a78ab6f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424481(v=office.15)
ms:contentKeyID: 55119934
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Add Fields to a View

This example shows how to customize a view by using the [Add(String)](https://msdn.microsoft.com/en-us/library/bb646040\(v=office.15\)) method of the [ViewFields](https://msdn.microsoft.com/en-us/library/bb645950\(v=office.15\)) collection to add fields to a view.

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


You can specify which Outlook item properties are displayed in a view by adding one or more properties to the ViewFields collection for only the [CardView](https://msdn.microsoft.com/en-us/library/bb609216\(v=office.15\)) and [TableView](https://msdn.microsoft.com/en-us/library/bb608854\(v=office.15\)) objects. For other derived view objects such as [BusinessCardView](https://msdn.microsoft.com/en-us/library/bb646315\(v=office.15\)), [CalendarView](https://msdn.microsoft.com/en-us/library/bb622874\(v=office.15\)), [IconView](https://msdn.microsoft.com/en-us/library/bb612031\(v=office.15\)), and [TimelineView](https://msdn.microsoft.com/en-us/library/bb609455\(v=office.15\)) objects, use other methods of determining which Outlook item properties are displayed within the view. For example, the fields displayed for the BusinessCardView object are determined by the Electronic Business Card (EBC) layout associated with each displayed Outlook item.

To get the ViewFields collection for a view, use the ViewFields property of the associated View object (for example, the CardView or TableView objects). The Add method of the ViewFields collection is used to create a [ViewField](https://msdn.microsoft.com/en-us/library/bb610583\(v=office.15\)) object that represents the Outlook item property to be displayed in the view. A ViewField object not only identifies an Outlook item property to display within the view, but it also describes how the values for that property should be displayed. You can change how individual column properties are displayed in a view by modifying the [ColumnFormat](https://msdn.microsoft.com/en-us/library/bb646462\(v=office.15\)) property of the ViewField object.

In the following code example, ModifyMeetingRequestsView gets the TableView object that represents all the views from the user’s Inbox that are “Meeting Requests” views. The example then uses the Add method to add the “Start” and “End” fields to the ViewFields object that corresponds to the TableView object. It also changes the label for the “From” field to “Organized By”. ModifyMeetingRequestsView then saves the modified TableView object.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void ModifyMeetingRequestsView()
{
    Outlook.TableView tableView = null;
    Outlook.ViewField startField = null;
    Outlook.ViewField endField = null;
    Outlook.ViewField fromField = null;
    try
    {
        tableView =
            Application.Session.GetDefaultFolder(
            Outlook.OlDefaultFolders.olFolderInbox)
            .Views["Meeting Requests"] as Outlook.TableView;
    }
    catch { }
    if (tableView != null)
    {
        try
        {
            startField = tableView.ViewFields["Start"];
        }
        catch{}
        if (startField == null)
        {
            startField = tableView.ViewFields.Add("Start");
        }
        try
        {
            endField = tableView.ViewFields["End"];
        }
        catch{}
        if (endField == null)
        {
            endField = tableView.ViewFields.Add("End");
        }
        try
        {
            fromField = tableView.ViewFields["From"];
        }
        catch{}
        if (fromField != null)
        {
            fromField.ColumnFormat.Label = "Organized By";
        }
        try
        {
            tableView.Save();
        }
        catch (Exception ex)
        {
            Debug.WriteLine(ex.Message);
        }
    }
}
```

## See also



[Views](views.md)

