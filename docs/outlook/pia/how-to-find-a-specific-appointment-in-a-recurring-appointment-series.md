---
title: Find a specific appointment in a recurring appointment series
TOCTitle: Find a specific appointment in a recurring appointment series
ms:assetid: 01f55f04-7245-4325-a354-50a6eb270a31
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184586(v=office.15)
ms:contentKeyID: 55119812
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Find a specific appointment in a recurring appointment series

This example shows how to return an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object that represents a specific appointment in a recurring appointment series.

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


To find an instance of a recurring appointment that occurs at a specified date and time, use the [GetOccurrence(DateTime)](https://msdn.microsoft.com/en-us/library/bb622806\(v=office.15\)) method of the [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object to return an AppointmentItem object.

When you work with recurring appointment items, you should release any prior references, obtain new references to the recurring appointment item before you access or modify the item, and release these references as soon as you are finished and have saved the changes. This practice applies to the recurring AppointmentItem object, and any [Exception](https://msdn.microsoft.com/en-us/library/bb610440\(v=office.15\)) or [RecurrencePattern](https://msdn.microsoft.com/en-us/library/bb608903\(v=office.15\)) object. To release a reference in Visual Basic, set that existing object to Nothing. In C\#, explicitly release the memory for that object.

Note that even after you release your reference and attempt to obtain a new reference, if there is still an active reference (held by another add-in or Outlook) to one of the above objects, your new reference will still point to an out-of-date copy of the object. Therefore, it is important that you release your references as soon as you are finished with the recurring appointment.

In the following code example, CheckOccurrenceExample uses the recurring appointment that was created in the code example in [Create a Recurring Appointment That Has a Weekly Pattern](how-to-create-a-recurring-appointment-that-has-a-weekly-pattern.md). It then calls the GetOccurrence method to determine whether the recurring appointment starts on the specified date and time. To ensure that the procedure will continue even if the provided information does not match the start date and time of an instance of the recurring appointment, the example uses a try…catch block. After calling the GetOccurrence method on every appointment in the recurring appointment series, CheckOccurrenceExample tests the singleAppt variable to determine whether it is set to a null reference, indicating that the method failed and did not return an AppointmentItem object.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void CheckOccurrenceExample()
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
            Outlook.AppointmentItem singleAppt =
                pattern.GetOccurrence(DateTime.Parse(
                "7/21/2006 2:00 PM"))
                as Outlook.AppointmentItem;
            if (singleAppt != null)
            {
                Debug.WriteLine("7/21/2006 2:00 PM occurrence found.");
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

- [Appointments](appointments.md)

