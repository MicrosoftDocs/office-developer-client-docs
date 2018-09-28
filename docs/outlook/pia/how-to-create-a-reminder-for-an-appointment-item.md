---
title: 'Create a Reminder for an Appointment Item'
TOCTitle: 'Create a Reminder for an Appointment Item'
ms:assetid: 85e772f0-65ac-4abc-8286-9099882a2400
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184623(v=office.15)
ms:contentKeyID: 55119814
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Create a Reminder for an Appointment Item

This example shows how to use the [ReminderSet](https://msdn.microsoft.com/en-us/library/bb624262\(v=office.15\)) property to create a reminder for an appointment item.

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


Outlook provides a way to set a reminder for an appointment by using the [ReminderSet](https://msdn.microsoft.com/en-us/library/bb624262\(v=office.15\)) property of the [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object. This property indicates whether a reminder has been created for the appointment. Setting the ReminderSet property to true creates a reminder, and setting it to false removes the reminder.

In the following code example, ReminderExample creates a reminder on a private appointment for wine tasting in Napa, California, and sets the reminder to occur two hours before the appointment starts. First, ReminderExample creates an Outlook AppointmentItem object. It then sets the [Sensitivity](https://msdn.microsoft.com/en-us/library/bb623503\(v=office.15\)) property for the item to [olPrivate](https://msdn.microsoft.com/en-us/library/bb645125\(v=office.15\)). This indicates that the appointment is a private appointment. After setting other properties of the appointment, such as [Start](https://msdn.microsoft.com/en-us/library/bb647263\(v=office.15\)) and [End](https://msdn.microsoft.com/en-us/library/bb623715\(v=office.15\)) times, ReminderExample sets the [ReminderMinutesBeforeStart](https://msdn.microsoft.com/en-us/library/bb644528\(v=office.15\)) property to indicate the number of minutes that the reminder will appear before the start of the appointment. In this case, ReminderMinutesBeforeStart is set to 120 minutes (two hours).

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void ReminderExample()
{
    Outlook.AppointmentItem appt = Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.Subject = "Wine Tasting";
    appt.Location = "Napa CA";
    appt.Sensitivity = Outlook.OlSensitivity.olPrivate;
    appt.Start = DateTime.Parse("10/21/2006 10:00 AM");
    appt.End = DateTime.Parse("10/21/2006 3:00 PM");
    appt.ReminderSet = true;
    appt.ReminderMinutesBeforeStart = 120;
    appt.Save();
}
```

## See also



[Appointments](appointments.md)

