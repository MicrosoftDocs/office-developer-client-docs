---
title: Create an appointment that is an all-day event
TOCTitle: Create an appointment that is an all-day event
ms:assetid: a0d3baeb-6ed5-41b6-bef5-d6c1bb56fee3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184629(v=office.15)
ms:contentKeyID: 55119806
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Create an appointment that is an all-day event

This example shows how use the [AllDayEvent](https://msdn.microsoft.com/en-us/library/bb610279\(v=office.15\)) property to create an appointment that is an all-day event.

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


An event is different from a regular appointment because it is an activity that lasts 24 hours or longer. Examples of events include trade shows, seminars, or vacations. Events and annual events do not appear as occupied blocks of time in the user’s calendar. Instead, they appear as banners. You can see the banners at the top of a calendar day or week view. For an all-day appointment, by default, the user’s time is displayed as busy when viewed by other people, but the user’s time is displayed as free for an event or annual event.

To create an all-day event programmatically, set the [AllDayEvent](https://msdn.microsoft.com/en-us/library/bb610279\(v=office.15\)) property of the [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object to true. Then set the [Start](https://msdn.microsoft.com/en-us/library/bb647263\(v=office.15\)) and [End](https://msdn.microsoft.com/en-us/library/bb623715\(v=office.15\)) properties of the AppointmentItem. If you set the AllDayEvent property to true and do not set the Start and End properties, the event will occur today, and it will be an appointment, showing a busy status on your calendar. You must set the Start and End properties if you want the event to occur on a future date.

> [!NOTE]
> To make the appointment an all-day event, you must set the Start property to 12:00 A.M. (midnight) on the day you want the event to begin, and set End property to 12:00 A.M. on the day after you want the event to end. If you set the Start or End time to a date and time value other than 12:00 A.M., the appointment will become a multiday appointment instead of an all-day event. 
>
> For example, if your event duration is only one day, set the Start property to 12:00 A.M. on the day you want the event to begin, and set the End property to 12:00 A.M. on the following day. You should always set the End property to 12:00 A.M. on a date that is more than one day after the start date.

In the following code example, AllDayEventExample creates an all-day event that begins on June 11, 2007, and ends on June 15, 2007. Note that the End property for the appointment is set to 12:00 A.M. on June 16, 2007.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void AllDayEventExample()
{
    Outlook.AppointmentItem appt = Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.Subject = "Developer's Conference";
    appt.AllDayEvent = true;
    appt.Start = DateTime.Parse("6/11/2007 12:00 AM");
    appt.End = DateTime.Parse("6/16/2007 12:00 AM");
    appt.Display(false);
}
```

## See also

- [Appointments](appointments.md)

