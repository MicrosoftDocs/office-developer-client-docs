---
title: Automatically accept a meeting request
TOCTitle: Automatically accept a meeting request
ms:assetid: 3c729bcf-4c85-4efa-af79-2c94d55c2042
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184604(v=office.15)
ms:contentKeyID: 55119874
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Automatically accept a meeting request

This example shows how to use the [Respond(OlMeetingResponse, Object, Object)](https://msdn.microsoft.com/en-us/library/bb647086\(v=office.15\)) method to automatically accept a meeting request.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).


A [MeetingItem](https://msdn.microsoft.com/en-us/library/bb645703\(v=office.15\)) object represents a request to add an appointment, represented by an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object, to a recipient’s calendar. To respond to a meeting request, use the [GetAssociatedAppointment(Boolean)](https://msdn.microsoft.com/en-us/library/bb652725\(v=office.15\)) method to obtain the **AppointmentItem** associated with the meeting request. Then use the [Respond(OlMeetingResponse, Object, Object)](https://msdn.microsoft.com/en-us/library/bb647086\(v=office.15\)) method of the **AppointmentItem** to notify the meeting organizer whether the meeting has been accepted, declined, or tentatively added to the recipient’s calendar. The **Respond** method accepts three parameters. 

The *Response* parameter indicates whether the response is accept, decline, or tentative. The fNoUI and fAdditionalTextDialog parameters are **bool** values that determine whether a response will be sent, and whether the user may or may not edit the response, respectively. In the following code example, AutoAcceptMeetingRequests enumerates through every **MeetingItem** object to get the associated **AppointmentItem**. AutoAcceptMeetingRequests then uses the **Respond** method with the *fNoUI* parameter set to **true** to indicate that a response will be sent automatically to accept the meeting request.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void AutoAcceptMeetingRequests()
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
                true, Type.Missing);
            mtgResponse.Send();
        }
    }
}
```

## See also

- [Meeting requests](meeting-requests.md)

