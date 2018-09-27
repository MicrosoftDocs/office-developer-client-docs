---
title: 'How to: Find the Appointment Item Associated with a Meeting Request'
TOCTitle: 'How to: Find the Appointment Item Associated with a Meeting Request'
ms:assetid: ff356fcf-0980-4567-8570-4bbcb14381e7
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184658(v=office.15)
ms:contentKeyID: 55119875
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Find the Appointment Item Associated with a Meeting Request

This example shows how to use the [GetAssociatedAppointment(Boolean)](https://msdn.microsoft.com/en-us/library/bb652725\(v=office.15\)) method to find the appointment that is associated with a meeting request.

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


A [MeetingItem](https://msdn.microsoft.com/en-us/library/bb645703\(v=office.15\)) object does not represent an appointment, but a message that contains a request to add an appointment to the recipient’s calendar. In the following code example, MeetingRequestExample uses the [GetAssociatedAppointment(Boolean)](https://msdn.microsoft.com/en-us/library/bb652725\(v=office.15\)) method of the MeetingItem object on each MeetingItem retrieved from the user’s Inbox. The returned [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object is then used to write the subject of the appointment to the trace listeners of the [Listeners](http://msdn.microsoft.com/en-us/library/system.diagnostics.debug.listeners.aspx) collection.


> [!NOTE]
> <P>Note that GetAssociatedAppointment argument is set to false so that the appointment is not added to the user’s calendar.</P>



If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void MeetingRequestsExample()
{
    Outlook.Folder folder = Application.Session.
        GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    string filter = "[MessageClass] = " +
        "'IPM.Schedule.Meeting.Request'";
    Outlook.Items items = folder.Items.Restrict(filter);
    foreach (Outlook.MeetingItem request in items)
    {
        Outlook.AppointmentItem appt =
            request.GetAssociatedAppointment(false);
        if (appt != null)
        {
            Debug.WriteLine(appt.Subject);
        }
    }
}
```

## See also

#### Other resources

[Meeting Requests](meeting-requests.md)

