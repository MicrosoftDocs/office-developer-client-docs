---
title: Create an annual recurring appointment that uses a YearNth pattern
TOCTitle: Create an annual recurring appointment that uses a YearNth pattern
ms:assetid: 5fb2ad0b-248c-417d-8868-52e0550d970f
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184611(v=office.15)
ms:contentKeyID: 55119811
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Create an annual recurring appointment that uses a YearNth pattern

This example shows how to create an appointment for which the annual recurrence pattern is a specific day such as the first Monday in June.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

If you want to create an annual appointment that recurs on a specific day of the week during a specific month (for example, the first Monday in June), you must use YearNth recurrences. To set a YearNth recurrence, you must first set the [RecurrenceType](https://msdn.microsoft.com/en-us/library/bb623463\(v=office.15\)) property of the [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object to olRecursYearNth. Then set the [DayOfWeekMask](https://msdn.microsoft.com/en-us/library/bb609163\(v=office.15\)) property to specify on which day of the week the appointment should recur, and the [Instance](https://msdn.microsoft.com/en-us/library/bb645269\(v=office.15\)) property to specify the Nth occurrence of the specified day of the week (for example, the third Tuesday) during a specified month for the yearly pattern.

When you work with recurring appointment items, you should release any prior references, obtain new references to the recurring appointment item before you access or modify the item, and release these references as soon as you are finished and have saved the changes. This practice applies to the recurring **AppointmentItem** object, and any [Exception](https://msdn.microsoft.com/en-us/library/bb610440\(v=office.15\)) or [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object. To release a reference in Visual Basic, set that existing object to Nothing. In C\#, explicitly release the memory for that object.

Note that even after you release your reference and attempt to obtain a new reference, if there is still an active reference (held by another add-in or Outlook) to one of the above objects, your new reference will still point to an out-of-date copy of the object. Therefore, it is important that you release your references as soon as you are finished with the recurring appointment.

In the following code example, RecurringYearNthAppointment creates an appointment that has a YearNth recurrence pattern. RecurringYearNthAppointment first creates a recurring appointment by creating an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object. Next, it gets the appointment’s recurrence pattern by using the [GetRecurrencePattern()](https://msdn.microsoft.com/en-us/library/bb652582\(v=office.15\)) method. It then sets the following RecurrencePattern properties: RecurrenceType, DayOfWeekMask, [MonthOfYear](https://msdn.microsoft.com/en-us/library/bb610515\(v=office.15\)), [Instance](https://msdn.microsoft.com/en-us/library/bb645269\(v=office.15\)), [Occurrences](https://msdn.microsoft.com/en-us/library/bb611303\(v=office.15\)), [Duration](https://msdn.microsoft.com/en-us/library/bb644889\(v=office.15\)), [PatternStartDate](https://msdn.microsoft.com/en-us/library/bb624492\(v=office.15\)), [StartTime](https://msdn.microsoft.com/en-us/library/bb646324\(v=office.15\)), and [EndTime](https://msdn.microsoft.com/en-us/library/bb644544\(v=office.15\)). The MonthOfYear property can take a numerical value of 1 through 12, where each number represents the corresponding month. Once the properties are set, RecurringYearNthAppointment saves the appointment, and then displays it with the pattern "Occurs the first Monday of June effective 6/1/2007 until 6/6/2016 from 2:00 PM to 5:00 PM."

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void RecurringYearNthAppointment()
{
    Outlook.AppointmentItem appt = Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.Subject = "Recurring YearNth Appointment";
    Outlook.RecurrencePattern pattern = appt.GetRecurrencePattern();
    pattern.RecurrenceType = Outlook.OlRecurrenceType.olRecursYearNth;
    pattern.DayOfWeekMask = Outlook.OlDaysOfWeek.olMonday;
    pattern.MonthOfYear = 6;
    pattern.Instance = 1;
    pattern.Occurrences = 10;
    pattern.Duration = 180;
    pattern.PatternStartDate = DateTime.Parse("6/1/2007");
    pattern.StartTime = DateTime.Parse("2:00:00 PM");
    pattern.EndTime = DateTime.Parse("5:00:00 PM");
    appt.Save();
    appt.Display(false);
}
```

## See also

- [Appointments](appointments.md)

