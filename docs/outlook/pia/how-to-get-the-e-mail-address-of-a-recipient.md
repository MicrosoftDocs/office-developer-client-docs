---
title: 'How to: Get the E-Mail Address of a Recipient'
TOCTitle: 'How to: Get the E-Mail Address of a Recipient'
ms:assetid: e585811b-a298-496f-ba79-df7d46526169
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184647(v=office.15)
ms:contentKeyID: 55119879
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Get the E-Mail Address of a Recipient

This example shows how to get the Simple Mail Transfer Protocol (SMTP) address of a recipient.

## Example

In the following the code example, the GetSMTPAddressForRecipients method takes a [MailItem](https://msdn.microsoft.com/en-us/library/bb643865\(v=office.15\)) object as an input argument and then displays the SMTP address of each recipient for that mail item. The method first retrieves the [Recipients](https://msdn.microsoft.com/en-us/library/bb646361\(v=office.15\)) collection that represents the set of recipients specified for the mail item. For each [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) in that Recipients collection, the method then obtains the [PropertyAccessor](https://msdn.microsoft.com/en-us/library/bb646034\(v=office.15\)) object that corresponds to that Recipient object. Finally, the method uses the [PropertyAccessor](https://msdn.microsoft.com/en-us/library/bb623797\(v=office.15\)) property to get the value of the MAPI property http://schemas.microsoft.com/mapi/proptag/0x39FE001E, which maps to the PR\_SMTP\_ADDRESS ([PidTagSmtpAddress](https://msdn.microsoft.com/en-us/library/cc842421\(v=office.15\))) property of the recipient.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void GetSMTPAddressForRecipients(Outlook.MailItem mail)
{
    const string PR_SMTP_ADDRESS =
        "http://schemas.microsoft.com/mapi/proptag/0x39FE001E";
    Outlook.Recipients recips = mail.Recipients;
    foreach (Outlook.Recipient recip in recips)
    {
        Outlook.PropertyAccessor pa = recip.PropertyAccessor;
        string smtpAddress =
            pa.GetProperty(PR_SMTP_ADDRESS).ToString();
        Debug.WriteLine(recip.Name + " SMTP=" + smtpAddress);
    }
}
```

## See also



[Recipients](recipients.md)

