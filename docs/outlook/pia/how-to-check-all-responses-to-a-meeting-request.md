﻿---
title: Check all responses to a meeting request
TOCTitle: Check all responses to a meeting request
ms:assetid: ebe10e5a-7f04-447a-bfc1-aa8a726cb0b3
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184650(v=office.15)
ms:contentKeyID: 55119881
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Check all responses to a meeting request

This example shows how to check the status of each recipient’s response to a meeting request.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

In the following code example, CheckAttendeeStatus enumerates the [Recipients](https://msdn.microsoft.com/en-us/library/bb646361\(v=office.15\)) collection for the [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object that represents a meeting request and examines the [MeetingResponseStatus](https://msdn.microsoft.com/en-us/library/bb645283\(v=office.15\)) property of each [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) object. Each **Recipient** object represents a recipient of the meeting request. The value of the **MeetingResponseStatus** property can be one of the following [OlResponseStatus](https://msdn.microsoft.com/en-us/library/bb644655\(v=office.15\)) enumeration values:

- [olResponseAccepted](https://msdn.microsoft.com/en-us/library/bb644655\(v=office.15\))
- [olResponseDeclined](https://msdn.microsoft.com/en-us/library/bb644655\(v=office.15\))
- [olResponseNone](https://msdn.microsoft.com/en-us/library/bb644655\(v=office.15\))
- [olResponseNotResponded](https://msdn.microsoft.com/en-us/library/bb644655\(v=office.15\))
- [olResponseOrganized](https://msdn.microsoft.com/en-us/library/bb644655\(v=office.15\))
- [olResponseTentative](https://msdn.microsoft.com/en-us/library/bb644655\(v=office.15\))

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void CheckAttendeeStatus()
{
    Outlook.AppointmentItem appt = Application.Session.
        GetDefaultFolder(Outlook.OlDefaultFolders.olFolderCalendar).
        Items.Find("[Subject]='Sales Strategy FY2007'")
        as Outlook.AppointmentItem;
    if (appt != null)
    {
        foreach (Outlook.Recipient recip in appt.Recipients)
        {
            switch (recip.MeetingResponseStatus)
            {
                case Outlook.OlResponseStatus.olResponseAccepted:
                    Debug.WriteLine("Accepted: " + recip.Name);
                    break;
                case Outlook.OlResponseStatus.olResponseTentative:
                    Debug.WriteLine("Tentative: " + recip.Name);
                    break;
                case Outlook.OlResponseStatus.olResponseDeclined:
                    Debug.WriteLine("Declined: " + recip.Name);
                    break;
                case Outlook.OlResponseStatus.olResponseOrganized:
                    Debug.WriteLine("Organizer: " + recip.Name);
                    break;
                case Outlook.OlResponseStatus.olResponseNone:
                    Debug.WriteLine("None: " + recip.Name);
                    break;
                case Outlook.OlResponseStatus.olResponseNotResponded:
                    Debug.WriteLine("Not responded: " + recip.Name);
                    break;
            }
        }
    }
}
```

## See also

- [Meeting requests](meeting-requests.md)

