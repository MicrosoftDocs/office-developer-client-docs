---
title: Create a recurring appointment that has a weekly pattern
TOCTitle: Create a recurring appointment that has a weekly pattern
ms:assetid: 20b46b26-e278-451b-9e35-36683205d164
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184595(v=office.15)
ms:contentKeyID: 55119810
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Create a recurring appointment that has a weekly pattern

This example shows how to create a recurring appointment that has a weekly pattern (for example, an appointment that occurs every Monday, Wednesday, and Friday).

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).


When you create a new recurring appointment, the recurrence pattern is based on the time you specify when you create the appointment. For example, if you create an appointment that recurs daily at 1:00 PM, the appointment will recur only at 1:00 PM on a daily basis. To change the recurrence pattern of an appointment, set the properties of the appointment’s [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object. Set the [RecurrenceType](https://msdn.microsoft.com/en-us/library/bb623463\(v=office.15\)) property of the RecurrencePattern object before setting other RecurrencePattern properties. The following table shows valid RecurrencePattern properties for a given RecurrenceType (specified by the [OlRecurrenceType](https://msdn.microsoft.com/en-us/library/bb647129\(v=office.15\)) enumeration).

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>OlRecurrenceType value</p></th>
<th><p>Valid RecurrencePattern properties</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>olRecursDaily</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/bb644889(v=office.15)">Duration</a>, <a href="https://msdn.microsoft.com/en-us/library/bb644544(v=office.15)">EndTime</a>, <a href="https://msdn.microsoft.com/en-us/library/bb624287(v=office.15)">Interval</a>, <a href="https://msdn.microsoft.com/en-us/library/bb646849(v=office.15)">NoEndDate</a>, <a href="https://msdn.microsoft.com/en-us/library/bb611303(v=office.15)">Occurrences</a>, <a href="https://msdn.microsoft.com/en-us/library/bb624492(v=office.15)">PatternStartDate</a>, <a href="https://msdn.microsoft.com/en-us/library/bb609279(v=office.15)">PatternEndDate</a>, <a href="https://msdn.microsoft.com/en-us/library/bb646324(v=office.15)">StartTime</a></p></td>
</tr>
<tr class="even">
<td><p>olRecursWeekly</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/bb609163(v=office.15)">DayOfWeekMask</a>, Duration, EndTime, Interval, NoEndDate, Occurrences, PatternStartDate, PatternEndDate, StartTime</p></td>
</tr>
<tr class="odd">
<td><p>olRecursMonthly</p></td>
<td><p><a href="https://msdn.microsoft.com/en-us/library/bb622604(v=office.15)">DayOfMonth</a>, Duration, EndTime, Interval, NoEndDate, Occurrences, PatternStartDate, PatternEndDate, StartTime</p></td>
</tr>
<tr class="even">
<td><p>olRecursMonthNth</p></td>
<td><p>DayOfWeekMask, Duration, EndTime, Interval, <a href="https://msdn.microsoft.com/en-us/library/bb645269(v=office.15)">Instance</a>, NoEndDate, Occurrences, PatternStartDate, PatternEndDate, StartTime</p></td>
</tr>
<tr class="odd">
<td><p>olRecursYearly</p></td>
<td><p>DayOfMonth, Duration, EndTime, Interval, <a href="https://msdn.microsoft.com/en-us/library/bb610515(v=office.15)">MonthOfYear</a>, NoEndDate, Occurrences, PatternStartDate, PatternEndDate, StartTime</p></td>
</tr>
<tr class="even">
<td><p>olRecursYearNth</p></td>
<td><p>DayOfWeekMask, Duration, EndTime, Interval, Instance, NoEndDate, Occurrences, PatternStartDate, PatternEndDate, StartTime</p></td>
</tr>
</tbody>
</table>


When you work with recurring appointment items, you should release any prior references, obtain new references to the recurring appointment item before you access or modify the item, and release these references as soon as you are finished and have saved the changes. This practice applies to the recurring **AppointmentItem** object, and any [Exception](https://msdn.microsoft.com/en-us/library/bb610440\(v=office.15\)) or [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object. To release a reference in Visual Basic, set that existing object to Nothing. In C\#, explicitly release the memory for that object.

Note that even after you release your reference and attempt to obtain a new reference, if there is still an active reference (held by another add-in or Outlook) to one of the above objects, your new reference will still point to an out-of-date copy of the object. Therefore, it is important that you release your references as soon as you are finished with the recurring appointment.

In the following code example, RecurringAppointmentEveryMondayWednesdayFriday creates an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object, and then calls [GetRecurrencePattern()](https://msdn.microsoft.com/en-us/library/bb652582\(v=office.15\)) to get the newly created appointment’s RecurrencePattern object. RecurringAppointmentEveryMondayWednesdayFriday then sets the RecurrenceType, DayOfWeekMask, PatternStartDate, PatternEndDate, Duration, StartTime, EndTime, and Subject properties, saves the appointment, and finally displays the appointment with the pattern "Occurs every Monday, Wednesday, and Friday effective 7/10/2006 until 8/25/2006 from 2:00 PM to 3:00 PM."

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void RecurringAppointmentEveryMondayWednesdayFriday()
{
    Outlook.AppointmentItem appt = Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.Subject = "Recurring Appointment DaysOfWeekMask Example";
    Outlook.RecurrencePattern pattern = appt.GetRecurrencePattern();
    pattern.RecurrenceType = Outlook.OlRecurrenceType.olRecursWeekly;
    // Logical OR for DayOfWeekMask creates pattern
    pattern.DayOfWeekMask = Outlook.OlDaysOfWeek.olMonday |
        Outlook.OlDaysOfWeek.olWednesday |
        Outlook.OlDaysOfWeek.olFriday;
    pattern.PatternStartDate = DateTime.Parse("7/10/2006");
    pattern.PatternEndDate = DateTime.Parse("8/25/2006");
    pattern.Duration = 60;
    pattern.StartTime = DateTime.Parse("2:00:00 PM");
    pattern.EndTime = DateTime.Parse("3:00:00 PM");
    appt.Save();
    appt.Display(false);
}
```

## See also

- [Appointments](appointments.md)

