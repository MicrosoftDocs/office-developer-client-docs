---
title: 'Get Information About Multiple Accounts'
TOCTitle: 'Get Information About Multiple Accounts'
ms:assetid: 363f4058-3069-4ddc-b3ff-113a4dfd58c4
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184599(v=office.15)
ms:contentKeyID: 55119794
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Get Information About Multiple Accounts

Outlook supports a profile that contains one or more accounts that are connected to an Exchange Server. This example shows how to obtain and display miscellaneous information about each account in the current profile.

## Example

The following method, EnumerateAccounts, displays the account name, user name, and Simple Mail Transfer Protocol (SMTP) address for each account that is defined in the current profile. If the account is connected to an Exchange server, EnumerateAccounts displays the Exchange server name and version information. And if the account resides on a delivery store, EnumerateAccounts displays the name of the default delivery store for the account.

EnumerateAccounts accesses most of this information from the [Account](https://msdn.microsoft.com/en-us/library/bb645103\(v=office.15\)) object, except when the Account object does not contain information about the user name and SMTP address. In that case, EnumerateAccounts uses the [AddressEntry](https://msdn.microsoft.com/en-us/library/bb609728\(v=office.15\)) and [ExchangeUser](https://msdn.microsoft.com/en-us/library/bb609574\(v=office.15\)) objects. EnumerateAccounts obtains the AddressEntry object by using the [AddressEntry](https://msdn.microsoft.com/en-us/library/bb644359\(v=office.15\)) property of the [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) object obtained from the [CurrentUser](https://msdn.microsoft.com/en-us/library/ff184864\(v=office.15\)) property. EnumerateAccounts obtains the ExchangeUser object by using the [GetExchangeUser()](https://msdn.microsoft.com/en-us/library/bb611808\(v=office.15\)) method of the AddressEntry object. The following is the algorithm to obtain various information by using the Account, AddressEntry, and ExchangeUser objects:

  - If the Account object contains information about the user name and SMTP address, use the Account object to display the account name, user name, SMTP address, and Exchange server name and version information if the account is an Exchange account.

  - If the Account object does not contain information about the user name and SMTP address, proceed as follows:
    
      - If the account is not an Exchange account, use the AddressEntry object to display the user name and SMTP address.
    
      - If the account is an Exchange account, proceed as follows:
        
        1.  Use the Account object to display the account name, Exchange server name, and Exchange version information.
        
        2.  Use the ExchangeUser object to display the user name and SMTP address.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void EnumerateAccounts()
{
    Outlook.Accounts accounts =
        Application.Session.Accounts;
    foreach (Outlook.Account account in accounts)
    {
        try
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendLine("Account: " + account.DisplayName);
            if (string.IsNullOrEmpty(account.SmtpAddress)
                || string.IsNullOrEmpty(account.UserName))
            {
                Outlook.AddressEntry oAE =
                    account.CurrentUser.AddressEntry
                    as Outlook.AddressEntry;
                if (oAE.Type == "EX")
                {
                    Outlook.ExchangeUser oEU =
                        oAE.GetExchangeUser()
                        as Outlook.ExchangeUser;
                    sb.AppendLine("UserName: " +
                        oEU.Name);
                    sb.AppendLine("SMTP: " +
                        oEU.PrimarySmtpAddress);
                    sb.AppendLine("Exchange Server: " +
                        account.ExchangeMailboxServerName);
                    sb.AppendLine("Exchange Server Version: " +
                        account.ExchangeMailboxServerVersion); 
                }
                else
                {
                    sb.AppendLine("UserName: " +
                        oAE.Name);
                    sb.AppendLine("SMTP: " +
                        oAE.Address);
                }
            }
            else
            {
                sb.AppendLine("UserName: " +
                    account.UserName);
                sb.AppendLine("SMTP: " +
                    account.SmtpAddress);
                if(account.AccountType == 
                    Outlook.OlAccountType.olExchange)
                {
                    sb.AppendLine("Exchange Server: " +
                        account.ExchangeMailboxServerName);
                    sb.AppendLine("Exchange Server Version: " +
                        account.ExchangeMailboxServerVersion); 
                }
            }
            if(account.DeliveryStore !=null)
            {
                sb.AppendLine("Delivery Store: " +
                    account.DeliveryStore.DisplayName);
            }
            sb.AppendLine("---------------------------------");
            Debug.Write(sb.ToString());
        }
        catch (Exception ex)
        {
            Debug.WriteLine(ex.Message);
        }
    }
}
```

## See also



[Accounts](accounts.md)

