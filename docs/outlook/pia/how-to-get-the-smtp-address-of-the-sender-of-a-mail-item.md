---
title: 'Get the SMTP Address of the Sender of a Mail Item'
TOCTitle: 'Get the SMTP Address of the Sender of a Mail Item'
ms:assetid: 86e0c0aa-1696-4415-b25f-f9c1c29d88a9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184624(v=office.15)
ms:contentKeyID: 55119869
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Get the SMTP Address of the Sender of a Mail Item

This example gets the sender’s Simple Mail Transfer Protocol (SMTP) address for a mail item.

## Example

To determine the SMTP address for a received mail item, use the [SenderEmailAddress](https://msdn.microsoft.com/en-us/library/bb622746\(v=office.15\)) property of the [MailItem](https://msdn.microsoft.com/en-us/library/bb643865\(v=office.15\)) object. However, if the sender is internal to your organization, SenderEmailAddress does not return an SMTP address, and you must use the [PropertyAccessor](https://msdn.microsoft.com/en-us/library/bb646034\(v=office.15\)) object to return the sender’s SMTP address.

In the following code example, GetSenderSMTPAddress uses the PropertyAccessor object to obtain values that are not exposed directly in the Outlook object model. GetSenderSMTPAddress takes in a MailItem. If the value of the [SenderEmailType](https://msdn.microsoft.com/en-us/library/bb624136\(v=office.15\)) property of the received MailItem is "EX", the sender of the message resides on an Exchange server in your organization. GetSenderSMTPAddress uses the [Sender](https://msdn.microsoft.com/en-us/library/ff184720\(v=office.15\)) property of the MailItem object to get the sender, represented by the [AddressEntry](https://msdn.microsoft.com/en-us/library/bb609728\(v=office.15\)) object. If the AddressEntry object represents an Exchange user, the example calls the [GetExchangeUser()](https://msdn.microsoft.com/en-us/library/bb611808\(v=office.15\)) method to return the [ExchangeUser](https://msdn.microsoft.com/en-us/library/bb609574\(v=office.15\)) object of the AddressEntry object. GetSenderSMTPAddress then uses the [PrimarySmtpAddress](https://msdn.microsoft.com/en-us/library/bb645506\(v=office.15\)) property of the ExchangeUser object to return the SMTP address of the sender. If the AddressEntry object for the sender does not represent an ExchangeUser object, the [GetProperty(String)](https://msdn.microsoft.com/en-us/library/bb645726\(v=office.15\)) method of the PropertyAccessor object is used, with PR\_SMTP\_ADDRESS ([PidTagSmtpAddress](https://msdn.microsoft.com/en-us/library/cc842421\(v=office.15\))) as the argument, to return the sender’s SMTP address.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private string GetSenderSMTPAddress(Outlook.MailItem mail)
{
    string PR_SMTP_ADDRESS =
        @"http://schemas.microsoft.com/mapi/proptag/0x39FE001E";
    if (mail == null)
    {
        throw new ArgumentNullException();
    }
    if (mail.SenderEmailType == "EX")
    {
        Outlook.AddressEntry sender =
            mail.Sender;
        if (sender != null)
        {
            //Now we have an AddressEntry representing the Sender
            if (sender.AddressEntryUserType ==
                Outlook.OlAddressEntryUserType.
                olExchangeUserAddressEntry
                || sender.AddressEntryUserType ==
                Outlook.OlAddressEntryUserType.
                olExchangeRemoteUserAddressEntry)
            {
                //Use the ExchangeUser object PrimarySMTPAddress
                Outlook.ExchangeUser exchUser =
                    sender.GetExchangeUser();
                if (exchUser != null)
                {
                    return exchUser.PrimarySmtpAddress;
                }
                else
                {
                    return null;
                }
            }
            else
            {
                return sender.PropertyAccessor.GetProperty(
                    PR_SMTP_ADDRESS) as string;
            }
        }
        else
        {
            return null;
        }
    }
    else
    {
        return mail.SenderEmailAddress;
    }
}
```

## See also



[Mail](mail.md)

