---
title: 'Get the Organizer of a Meeting'
TOCTitle: 'Get the Organizer of a Meeting'
ms:assetid: 6a33db84-573b-4d1b-a91a-903f30630ec9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184615(v=office.15)
ms:contentKeyID: 55119872
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Get the Organizer of a Meeting

This example shows how to programmatically return the organizer of a meeting.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

In the following code example, GetMeetingOrganizer takes a parameter of type [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) that represents a meeting, and uses the [PropertyAccessor](https://msdn.microsoft.com/en-us/library/bb646034\(v=office.15\)) object and the [GetProperty(String)](https://msdn.microsoft.com/en-us/library/bb645726\(v=office.15\)) method to obtain the [EntryID](https://msdn.microsoft.com/en-us/library/bb645980\(v=office.15\)) for the AppointmentItem object. Once the EntryID is obtained, the example uses the [GetAddressEntryFromID(String)](https://msdn.microsoft.com/en-us/library/ff185034\(v=office.15\)) method to return the [AddressEntry](https://msdn.microsoft.com/en-us/library/bb609728\(v=office.15\)) object that represents the organizer of the meeting.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private Outlook.AddressEntry GetMeetingOrganizer(Outlook.AppointmentItem appt)
{
    if (appt == null)
    {
        throw new ArgumentNullException();
    }
    string PR_SENT_REPRESENTING_ENTRYID =
        @"http://schemas.microsoft.com/mapi/proptag/0x00410102";
    string organizerEntryID =
        appt.PropertyAccessor.BinaryToString(
            appt.PropertyAccessor.GetProperty(
            PR_SENT_REPRESENTING_ENTRYID));
    Outlook.AddressEntry organizer =
        Application.Session.
        GetAddressEntryFromID(organizerEntryID);
    if (organizer != null)
    {
        return organizer; 
    }
    else
    {
        return null;
    }
}
```

## See also



[Meeting Requests](meeting-requests.md)

