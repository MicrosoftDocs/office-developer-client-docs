﻿---
title: "Check a Manager's Response to a Meeting Request"
TOCTitle: "Check a Manager's Response to a Meeting Request"
ms:assetid: 7bdb2163-17e3-47b4-95e5-e051b90506c6
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184618(v=office.15)
ms:contentKeyID: 55119847
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Check a Manager's Response to a Meeting Request

This example illustrates how to use the [GetExchangeUser()](https://msdn.microsoft.com/en-us/library/bb611808\(v=office.15\)) and [GetExchangeUserManager()](https://msdn.microsoft.com/en-us/library/bb646656\(v=office.15\)) methods to check the status of the response of the current user's manager to a meeting request.

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


To determine whether a given recipient has accepted or declined a requested meeting, use the [MeetingResponseStatus](https://msdn.microsoft.com/en-us/library/bb645283\(v=office.15\)) property of the [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) object from the [Recipients](https://msdn.microsoft.com/en-us/library/bb646361\(v=office.15\)) collection associated with the [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) object.

In the following code example, CheckManagerResponseStatus takes in an AppointmentItem object as a parameter. CheckManagerResponseStatus gets the [ExchangeUser](https://msdn.microsoft.com/en-us/library/bb609574\(v=office.15\)) object by calling the GetExchangeUser method on the current user. CheckManagerResponseStatus then gets the ExchangeUser object that is associated with the current user’s manager by calling the GetExchangeUserManager method. By using the [CompareEntryIDs(String, String)](https://msdn.microsoft.com/en-us/library/bb646919\(v=office.15\)) method of the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object, the example then checks whether the Recipient object associated with the AppointmentItem object is the same as the ExchangeUser object that represents the user’s manager. If CompareEntryIDs returns true, the user’s manager is found in the Recipients collection, and CheckManagerResponseStatus returns the manager’s MeetingResponseStatus. If CompareEntryIDs returns false, CheckManagerResponseStatus returns a null reference.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private Object CheckManagerResponseStatus(Outlook.AppointmentItem appt)
{
    try
    {
        if (appt == null)
        {
            throw new ArgumentNullException();
        }
        Outlook.AddressEntry user =
            Application.Session.CurrentUser.AddressEntry;
        Outlook.ExchangeUser userEx = user.GetExchangeUser();
        if (userEx == null)
        {
            return null;
        }
        Outlook.ExchangeUser manager =
            userEx.GetExchangeUserManager();
        if (manager == null)
        {
            return null;
        }
        foreach (Outlook.Recipient recip in appt.Recipients)
        {
            if (Application.Session.CompareEntryIDs(
                recip.AddressEntry.ID, manager.ID))
            {
                return recip.MeetingResponseStatus;
            }
        }
        return null;
    }
    catch (Exception ex)
    {
        Debug.WriteLine(ex.Message);
        return null;
    }
}
```

## See also



[Exchange Users](exchange-users.md)
