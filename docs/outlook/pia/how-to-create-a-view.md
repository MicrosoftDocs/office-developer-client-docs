---
title: Create a view
TOCTitle: Create a view
ms:assetid: 2f8ad187-1030-420a-bc74-c327e3521550
ms:mtpsurl: https://msdn.microsoft.com/library/Ff424468(v=office.15)
ms:contentKeyID: 55119902
ms.date: 07/24/2014
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Create a view

This example shows how to use the [Add(String, OlViewType, OlViewSaveOption)](https://msdn.microsoft.com/library/bb643986\(v=office.15\)) method of the [Views](https://msdn.microsoft.com/library/bb644226\(v=office.15\)) collection to create a view for a [Folder](https://msdn.microsoft.com/library/bb645774\(v=office.15\)) object.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).


You can create customizable views that allow you to sort, group, and view data of all different types within the View Pane of the Outlook explorer window. You can also customize built-in views programmatically. The following table lists objects that represent Outlook views.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Object Name</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/bb646315(v=office.15)">BusinessCardView</a></p></td>
<td><p>Data is viewed as a series of electronic business card images.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/bb622874(v=office.15)">CalendarView</a></p></td>
<td><p>Data is viewed in a calendar format.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/bb609216(v=office.15)">CardView</a></p></td>
<td><p>Data is viewed in a series of cards.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/bb612031(v=office.15)">IconView</a></p></td>
<td><p>Data is viewed as Windows folder icons or explorer icons.</p></td>
</tr>
<tr class="odd">
<td><p><a href="https://msdn.microsoft.com/library/bb608854(v=office.15)">TableView</a></p></td>
<td><p>Data is viewed in a simple field-based table.</p></td>
</tr>
<tr class="even">
<td><p><a href="https://msdn.microsoft.com/library/bb609455(v=office.15)">TimelineView</a></p></td>
<td><p>Data is viewed in a customizable linear time line.</p></td>
</tr>
</tbody>
</table>


You can access properties and methods that are common to all views by using the [View](https://msdn.microsoft.com/library/bb647396\(v=office.15\)) object. However, to access certain properties that are not common to all views, you must cast the **View** object to a derived **View** object that the property you want to access belongs to. For example, to access the [HeadingsFont](https://msdn.microsoft.com/library/bb612522\(v=office.15\)) property of the **Cardview** object, cast the **View** object to the **Cardview** object. If you want to determine which type of view is represented by a particular **View** object, use the [ViewType](https://msdn.microsoft.com/library/bb623693\(v=office.15\)) property.

To create a new view, use the **Add** method of the **Views** collection for a **Folder** object. Then set the visibility for the view either at the time of creation, or at any time after the view is created. To set the visibility for the view at the time of creation, specify an [OlViewSaveOption](https://msdn.microsoft.com/library/bb647502\(v=office.15\)) constant in the *SaveOption* parameter of the **Add** method. To set the visibility at any time after the view is created, specify an **OlViewSaveOption** constant for the [SaveOption](https://msdn.microsoft.com/library/bb646426\(v=office.15\)) property of the **View** object. 

Adding a new view raises the [ViewAdd](https://msdn.microsoft.com/library/bb647550\(v=office.15\)) event of the **Views** collection. Once the view is created, customize the view programmatically by casting the **View** object to one of the derived objects and then making necessary changes. Use the **Save** method of the derived **View** object or the **View** object to save any changes to the view. Finally, use the **Apply** method of the derived **View** object or the **View** object to apply the view to the current [Explorer](https://msdn.microsoft.com/library/bb623678\(v=office.15\)) object. This raises the [ViewSwitch](https://msdn.microsoft.com/library/bb644066\(v=office.15\)) event of the **Explorer** object.

In the following code example, CreateMeetingRequestsView adds a new view named “Meeting Requests” to the user’s Inbox by casting the **View** object to a **TableView** object. CreateMeetingRequestsView then calls the **Add** method of the **Views** object with the *Name* parameter set to “Meeting Requests” and the *ViewType* parameter set to **olTableView**. The [Filter](https://msdn.microsoft.com/library/bb610296\(v=office.15\)) property of the **TableView** object is set to a DAV Searching and Locating (DASL) string that causes the view to display only when there are items that contain “IPM.Schedule” in the message class for the item. The new view is then saved and applied.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void CreateMeetingRequestsView()
{
    const string PR_MESSAGE_CLASS =
        "http://schemas.microsoft.com/mapi/proptag/0x001A001E";
    Outlook.Views views =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox).Views;
    Outlook.TableView tableView = (Outlook.TableView)
        views.Add("Meeting Requests",
        Outlook.OlViewType.olTableView,
        Outlook.OlViewSaveOption.olViewSaveOptionThisFolderEveryone);
    tableView.Filter = "\"" + PR_MESSAGE_CLASS + "\"" +
        " like 'IPM.Schedule%'";
    tableView.Save();
    tableView.Apply();
}
```

## See also

- [Views](views.md)

