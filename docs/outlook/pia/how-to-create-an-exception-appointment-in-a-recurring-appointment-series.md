﻿---
title: 'Create an Exception Appointment in a Recurring Appointment Series'
TOCTitle: 'Create an Exception Appointment in a Recurring Appointment Series'
ms:assetid: b7cd0975-4f44-453a-b878-ec55feeedc4e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184635(v=office.15)
ms:contentKeyID: 55119813
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Create an Exception Appointment in a Recurring Appointment Series

This example uses an [Exception](https://msdn.microsoft.com/en-us/library/bb610440\(v=office.15\)) object to create an exception to a standard recurrence pattern for an appointment.

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


Once you delete or change one appointment instance of a recurring appointment, Outlook creates an [Exception](https://msdn.microsoft.com/en-us/library/bb610440\(v=office.15\)) object. The Exception object allows you to create an exception to a standard recurrence pattern. The object’s properties contain the changes that were made to the appointment instance. The [Exceptions](https://msdn.microsoft.com/en-us/library/bb647601\(v=office.15\)) collection contains all of the Exception objects for a recurring appointment, and is associated with the appointment’s [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object.

To get the [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object that represents the exception to the original recurrence pattern of the recurring appointment, use the [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645648\(v=office.15\)) property of the Exception. By using the methods and properties of the returned AppointmentItem, you can set the properties of the appointment exception.

When you work with recurring appointment items, you should release any prior references, obtain new references to the recurring appointment item before you access or modify the item, and release these references as soon as you are finished and have saved the changes. This practice applies to the recurring AppointmentItem object, and any [Exception](https://msdn.microsoft.com/en-us/library/bb610440\(v=office.15\)) or [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object. To release a reference in Visual Basic, set that existing object to Nothing. In C\#, explicitly release the memory for that object.

Note that even after you release your reference and attempt to obtain a new reference, if there is still an active reference, held by another add-in or Outlook, to one of the above objects, your new reference will still point to an out-of-date copy of the object. Therefore, it is important that you release your references as soon as you are finished with the recurring appointment.

In the following code example, CreateExceptionExample changes the subject of the recurring appointment that was created in the topic [Find a Specific Appointment in a Recurring Appointment Series](how-to-find-a-specific-appointment-in-a-recurring-appointment-series.md), and then uses the AppointmentItem property of the resulting Exception object to retrieve the AppointmentItem that corresponds to the appointment exception. CreateExceptionExample then changes the start and end times of the appointment exception.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void CreateExceptionExample()
{
    Outlook.AppointmentItem appt = Application.Session.
        GetDefaultFolder(Outlook.OlDefaultFolders.olFolderCalendar).
        Items.Find(
        "[Subject]='Recurring Appointment DaysOfWeekMask Example'")
        as Outlook.AppointmentItem;
    if (appt != null)
    {
        try
        {
            Outlook.RecurrencePattern pattern =
                appt.GetRecurrencePattern();
            Outlook.AppointmentItem myInstance =
                pattern.GetOccurrence(DateTime.Parse(
                "7/21/2006 2:00 PM"))
                as Outlook.AppointmentItem;
            if (myInstance != null)
            {
                myInstance.Subject = "My Exception";
                myInstance.Save();
                Outlook.RecurrencePattern newPattern =
                    appt.GetRecurrencePattern();
                Outlook.Exception myException =
                    newPattern.Exceptions[1];
                if (myException != null)
                {
                    Outlook.AppointmentItem myNewInstance =
                        myException.AppointmentItem;
                    myNewInstance.Start =
                        DateTime.Parse("7/21/2006 1:00 PM");
                    myNewInstance.End =
                        DateTime.Parse("7/21/2006 2:00 PM");
                    myNewInstance.Save();
                }
            }
        }
        catch (Exception ex)
        {
            Debug.WriteLine(ex.Message);
        }
    }
}
```

## See also



[Appointments](appointments.md)
