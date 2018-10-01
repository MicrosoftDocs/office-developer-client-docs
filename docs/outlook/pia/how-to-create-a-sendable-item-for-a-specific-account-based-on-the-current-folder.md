---
title: Create a sendable item for a specific account based on the current folder
TOCTitle: Create a sendable item for a specific account based on the current folder
ms:assetid: 665ebdc5-2912-4d85-ac40-835c9ef9a439
ms:contentKeyID: 55119796
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Create a sendable item for a specific account based on the current folder

This topic contains two code examples that show how to create a sendable email item and meeting request, and then how to send them by using a specific account that is based on the current folder.

## Example

When you use the [CreateItem(OlItemType)](https://msdn.microsoft.com/en-us/library/bb610587\(v=office.15\)) method of the [Application](https://msdn.microsoft.com/en-us/library/bb646615\(v=office.15\)) object to create an Outlook item, the item is created for the primary account for that session. In a session where multiple accounts are defined in the profile, you can create an item for a specific IMAP, POP, or Exchange account. 

If there are multiple accounts in the current profile and you create a sendable item in the user interface, for example, by clicking **New Email** or **New Meeting**, an inspector displays a new mail item or meeting request in compose mode, and then you can select the account from which to send the item. 

This topic shows how to programmatically create a sendable item and send it by using a specific sending account. The topic has two code examples that show how to create a [MailItem](https://msdn.microsoft.com/en-us/library/bb643865\(v=office.15\)) and an [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) for a specific account that is determined by the current folder in the active explorer.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

In the first method, CreateMailItemFromAccount first identifies the appropriate account by matching the store of the current folder (obtained from the [Store](https://msdn.microsoft.com/en-us/library/bb612742\(v=office.15\)) property) with the default delivery store of each account (obtained with the [DeliveryStore](https://msdn.microsoft.com/en-us/library/ff185090\(v=office.15\)) property) that is defined in the [Accounts](https://msdn.microsoft.com/en-us/library/bb646328\(v=office.15\)) collection for the session. CreateMailItemFromAccount then creates the MailItem. 

To associate the item with the account, CreateMailItemFromAccount assigns the user of the account as the sender of the item by setting the account.CurrentUser.AddressEntry property to the [Sender](https://msdn.microsoft.com/en-us/library/ff184720\(v=office.15\)) property of the MailItem. Assigning the Sender property is the important step; if you do not specify the sender, the MailItem is created for the primary account by default. At the end of the method, CreateMailItemFromAccount displays the MailItem. Note that if the current folder is not on a delivery store, CreateMailItemFromAccount creates the MailItem for the primary account for the session.

```csharp
private void CreateMailItemFromAccount()
{
    Outlook.AddressEntry addrEntry = null;
    // Get the Store for CurrentFolder.
    Outlook.Folder folder =
        Application.ActiveExplorer().CurrentFolder 
        as Outlook.Folder;
    Outlook.Store store = folder.Store;
    Outlook.Accounts accounts =
        Application.Session.Accounts;
    // Enumerate accounts to find
    // account.DeliveryStore for store.
    foreach (Outlook.Account account in accounts)
    {
        if (account.DeliveryStore.StoreID == 
            store.StoreID)
        {
            addrEntry =
                account.CurrentUser.AddressEntry;
            break;
        }
    }
    // Create MailItem.
    Outlook.MailItem mail =
        Application.CreateItem(
        Outlook.OlItemType.olMailItem)
        as Outlook.MailItem;
    if (addrEntry != null)
    {
        // Set Sender property.
        mail.Sender = addrEntry;
        mail.Display(false);
    }
}
```

The next method, CreateMeetingRequestFromAccount, is similar to CreateMailItemFromAccount except that it creates an AppointmentItem instead of a MailItem. CreateMeetingRequestFromAccount first identifies the appropriate account by matching the store of the current folder (obtained from the [Store](https://msdn.microsoft.com/en-us/library/bb612742\(v=office.15\)) property) with the default delivery store of each account (obtained from the [DeliveryStore](https://msdn.microsoft.com/en-us/library/ff185090\(v=office.15\)) property) that is defined in the Accounts collection for the session. CreateMeetingRequestFromAccount then creates the AppointmentItem. 

To associate the item with the account, CreateMeetingRequestFromAccount assigns that account as the item's sending account by setting the [Account](https://msdn.microsoft.com/en-us/library/bb645103\(v=office.15\)) object to the [SendUsingAccount](https://msdn.microsoft.com/en-us/library/bb610680\(v=office.15\)) property of the AppointmentItem. Assigning the SendUsingAccount property is the important step; if you do not specify the account, the AppointmentItem is created for the primary account by default. At the end of the method, CreateMeetingRequestFromAccount displays the AppointmentItem. Note that if the current folder is not on a delivery store, CreateMeetingRequestFromAccount creates the AppointmentItem for the primary account for the session.

```csharp
private void CreateMeetingRequestFromAccount()
{
    Outlook.Account acct = null;
    Outlook.Folder folder =
        Application.ActiveExplorer().CurrentFolder
        as Outlook.Folder;
    Outlook.Store store = folder.Store;
    Outlook.Accounts accounts =
        Application.Session.Accounts;
    foreach (Outlook.Account account in accounts)
    {
        if (account.DeliveryStore.StoreID ==
            store.StoreID)
        {
            acct = account;
            break;
        }
    }
    Outlook.AppointmentItem appt =
        Application.CreateItem(
        Outlook.OlItemType.olAppointmentItem)
        as Outlook.AppointmentItem;
    appt.MeetingStatus = 
        Outlook.OlMeetingStatus.olMeeting;
    if (acct != null)
    {
        // Set SendUsingAccount property.
        appt.SendUsingAccount=acct;
        appt.Display(false);
    }
}
```

## See also

- [Accounts](accounts.md)

