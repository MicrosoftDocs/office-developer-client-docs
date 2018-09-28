﻿---
title: 'Prompt a User to Respond to a Meeting Request'
TOCTitle: 'Prompt a User to Respond to a Meeting Request'
ms:assetid: a0d69f82-8659-457d-9418-1a897a10882f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184630(v=office.15)
ms:contentKeyID: 55119877
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Prompt a User to Respond to a Meeting Request

This example shows how to prompt the user for a response to a meeting request, and to enable the user to edit the response before sending it.

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


The [Respond](https://msdn.microsoft.com/en-us/library/bb647086\(v=office.15\)) method of the [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object is used to notify the meeting organizer whether the meeting has been accepted, declined, or tentatively added to the recipient’s calendar. By using the Respond method, you can indicate whether you want to send the notification automatically, or whether you want to allow the user to edit the response before sending it. The Respond method accepts three parameters. The Response parameter indicates whether the response is accept, decline, or tentative. The fNoUI and fAdditionalTextDialog parameters are bool values that indicate whether the response will be sent to the organizer, and whether the user can edit the body of the response before sending it, respectively. In the following code example, PromptUserMeetingRequest enumerates through the [MeetingItem](https://msdn.microsoft.com/en-us/library/bb645703\(v=office.15\)) objects to get the associated AppointmentItem objects, and then calls the Respond method with the fNoUI parameter set to false and the fAdditionalTextDialog parameter set to true. This allows the user to choose whether to send a response, and whether to edit the body of the response before sending it.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void PromptUserMeetingRequest()
{
    Outlook.MeetingItem mtgResponse;
    Outlook.Folder folder = Application.Session.
        GetDefaultFolder(Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    string filter = "[MessageClass] = " +
        "'IPM.Schedule.Meeting.Request'";
    Outlook.Items items = folder.Items.Restrict(filter);
    foreach (Outlook.MeetingItem request in items)
    {
        Outlook.AppointmentItem appt =
            request.GetAssociatedAppointment(true);
        if (appt != null)
        {
            mtgResponse = appt.Respond(
                Outlook.OlMeetingResponse.olMeetingAccepted,
                false, true);
        }
    }
}
```

## See also



[Meeting Requests](meeting-requests.md)
