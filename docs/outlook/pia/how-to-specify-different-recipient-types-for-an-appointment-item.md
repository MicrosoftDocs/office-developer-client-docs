﻿---
title: 'Specify Different Recipient Types for an Appointment Item'
TOCTitle: 'Specify Different Recipient Types for an Appointment Item'
ms:assetid: 83aedc8f-adc0-453d-8e71-1bb9aacc7993
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184622(v=office.15)
ms:contentKeyID: 55119807
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Specify Different Recipient Types for an Appointment Item

This example shows how to use the [OlMeetingRecipientType](https://msdn.microsoft.com/en-us/library/bb623431\(v=office.15\)) enumeration to specify different recipient types for an appointment item.

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


To add recipients to an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object that represents a meeting request, use the OlMeetingRecipientType enumeration to specify whether the recipient of the message is a required or optional attendee, or a resource (such as a room or equipment).

In the following code example, SetRecipientTypeForAppt creates an AppointmentItem object, sets properties for that object, and adds required and optional attendees. It also adds a conference room for the meeting. Note that the [MeetingStatus](https://msdn.microsoft.com/en-us/library/bb611417\(v=office.15\)) property is set to [olMeeting](https://msdn.microsoft.com/en-us/library/bb644590\(v=office.15\)), indicating that the appointment is a meeting request.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void SetRecipientTypeForAppt()
{
    Outlook.AppointmentItem appt =
        Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.Subject = "Customer Review";
    appt.MeetingStatus = Outlook.OlMeetingStatus.olMeeting;
    appt.Location = "36/2021";
    appt.Start = DateTime.Parse("10/20/2006 10:00 AM");
    appt.End = DateTime.Parse("10/20/2006 11:00 AM");
    Outlook.Recipient recipRequired =
        appt.Recipients.Add("Ryan Gregg");
    recipRequired.Type =
        (int)Outlook.OlMeetingRecipientType.olRequired;
    Outlook.Recipient recipOptional =
        appt.Recipients.Add("Peter Allenspach");
    recipOptional.Type =
        (int)Outlook.OlMeetingRecipientType.olOptional;
    Outlook.Recipient recipConf =
        appt.Recipients.Add("Conf Room 36/2021 (14) AV");
    recipConf.Type =
        (int)Outlook.OlMeetingRecipientType.olResource;
    appt.Recipients.ResolveAll();
    appt.Display(false);
}
```

## See also



[Appointments](appointments.md)
