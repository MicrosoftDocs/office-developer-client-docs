---
title: 'How to: Use the Select Names Dialog Box to Obtain and Assign Recipients to an Appointment'
TOCTitle: 'How to: Use the Select Names Dialog Box to Obtain and Assign Recipients to an Appointment'
ms:assetid: b9bcb341-1912-425c-8d75-ed5be233145a
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184636(v=office.15)
ms:contentKeyID: 55119878
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Use the Select Names Dialog Box to Obtain and Assign Recipients to an Appointment

This example shows how to use the **Select Names** dialog box to obtain and assign recipients to an appointment item.

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


To display the **Select Names** dialog box, call the [Display()](https://msdn.microsoft.com/en-us/library/bb646086\(v=office.15\)) method of the [SelectNamesDialog](https://msdn.microsoft.com/en-us/library/bb609866\(v=office.15\)) object. Once the **Select Names** dialog box is displayed to the user, code execution halts until the user clicks **OK** or closes the dialog box. To set initial recipients to display in the dialog box, or to get the recipients selected in the dialog box, use the [Recipients](https://msdn.microsoft.com/en-us/library/bb652601\(v=office.15\)) property of the SelectNamesDialog object. This returns a [Recipients](https://msdn.microsoft.com/en-us/library/bb646361\(v=office.15\)) collection that is associated with the SelectNamesDialog. To add a [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) object to the Recipients collection for the SelectNamesDialog, use the [Add](https://msdn.microsoft.com/en-us/library/bb612668\(v=office.15\)) method for the collection and specify the [Type](https://msdn.microsoft.com/en-us/library/bb611841\(v=office.15\)) property of the Recipient object.

In the following code example, DemoSelectNamesDialogRecipients creates an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object and sets some of its properties. It then creates a SelectNamesDialog and uses the [SetDefaultDisplayMode(OlDefaultSelectNamesDisplayMode)](https://msdn.microsoft.com/en-us/library/bb623783\(v=office.15\)) method to set a meeting display mode for the **Select Names** dialog box. The example populates the Resource recipient selector with the string "Conf Room 36/2739". Once the dialog box is displayed to the user, the code enumerates the Recipients collection that is associated with this instance of SelectNamesDialog and adds those recipients to the appointment that was created. Finally, the example displays the meeting request to the user.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void DemoSelectNamesDialogRecipients()
{
    Outlook.AppointmentItem appt = Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.MeetingStatus = Outlook.OlMeetingStatus.olMeeting;
    appt.Subject = "Team Morale Event";
    appt.Start = DateTime.Parse("5/17/2007 11:00 AM");
    appt.End = DateTime.Parse("5/17/2007 12:00 PM");
    Outlook.SelectNamesDialog snd =
        Application.Session.GetSelectNamesDialog();
    snd.SetDefaultDisplayMode(
        Outlook.OlDefaultSelectNamesDisplayMode.olDefaultMeeting);
    Outlook.Recipient confRoom =
        snd.Recipients.Add("Conf Room 36/2739");
    // Explicitly specify Recipient.Type.
    confRoom.Type = (int)Outlook.OlMeetingRecipientType.olResource;
    snd.Recipients.ResolveAll();
    snd.Display();
    // Add Recipients to meeting request.
    Outlook.Recipients recips = snd.Recipients;
    if (recips.Count > 0)
    {
        foreach (Outlook.Recipient recip in recips)
        {
            appt.Recipients.Add(recip.Name);
        }
    }
    appt.Recipients.ResolveAll();
    appt.Display(false);
}
```

## See also



[Recipients](recipients.md)

