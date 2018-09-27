---
title: 'How to: Create a Recurring Appointment by Using the Default Recurrence Pattern'
TOCTitle: 'How to: Create a Recurring Appointment by Using the Default Recurrence Pattern'
ms:assetid: 157bf1ae-2efe-4783-99ea-606722dde204
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184589(v=office.15)
ms:contentKeyID: 55119809
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Create a Recurring Appointment by Using the Default Recurrence Pattern

This example shows how to create a recurring appointment by using the default recurrence pattern.

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


When you create an appointment in Outlook, you are creating an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object. Your appointment is a recurring appointment if the [IsRecurring](https://msdn.microsoft.com/en-us/library/bb609491\(v=office.15\)) property of the AppointmentItem is set to true. IsRecurring cannot be set directly. However, you can create a recurring appointment by using the [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object. To create a recurring appointment programmatically, create an AppointmentItem object, call the [GetRecurrencePattern()](https://msdn.microsoft.com/en-us/library/bb652582\(v=office.15\)) method of the AppointmentItem object, and then save the AppointmentItem object. This creates an appointment that uses the default recurrence pattern, which occurs weekly on the day of the week for which the appointment was created, and has no end date. The RecurrencePattern object allows you to create recurring appointments at specified intervals—daily, weekly, monthly, or yearly. If you do not specify intervals for the RecurrencePattern object, Outlook will use the default recurrence pattern.

When you work with recurring appointment items, you should release any prior references, obtain new references to the recurring appointment item before you access or modify the item, and release these references as soon as you are finished and have saved the changes. This practice applies to the recurring AppointmentItem object, and any [Exception](https://msdn.microsoft.com/en-us/library/bb610440\(v=office.15\)) or [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object. To release a reference in Visual Basic, set that existing object to Nothing. In C\#, explicitly release the memory for that object.

Note that even after you release your reference and attempt to obtain a new reference, if there is still an active reference (held by another add-in or Outlook) to one of the above objects, your new reference will still point to an out-of-date copy of the object. Therefore, it is important that you release your references as soon as you are finished with the recurring appointment.

In the following example, CreateRecurringAppointment creates an AppointmentItem object. It then calls GetRecurrencePattern. GetRecurrencePattern returns a RecurrencePattern object, and the AppointmentItem is saved. This creates a recurring appointment that uses the default recurrence pattern.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void CreateRecurringAppointment()
{
    Outlook.AppointmentItem appt = Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.Subject = "Weekly Extensibility Team Meeting";
    Outlook.RecurrencePattern pattern = appt.GetRecurrencePattern();
    appt.Save();
}
```

## See also



[Appointments](appointments.md)

