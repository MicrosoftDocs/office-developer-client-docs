---
title: 'Get the Account for a Folder'
TOCTitle: 'Get the Account for a Folder'
ms:assetid: 3706be15-f746-4d0d-9ffe-d6f46b2004dc
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184600(v=office.15)
ms:contentKeyID: 55119793
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Get the Account for a Folder

This example gets the account that is associated with a folder in the current session.

## Example

In the following code example, the DisplayAccountForCurrentFolder function calls the GetAccountForFolder function to identify the account whose default delivery store hosts the current folder, and then displays the name of the folder. GetAccountForFolder matches the store of the current folder (obtained from the [Store](https://msdn.microsoft.com/en-us/library/bb612742\(v=office.15\)) property) with the default delivery store of each account (obtained with the [DeliveryStore](https://msdn.microsoft.com/en-us/library/ff185090\(v=office.15\)) property) that is defined in the [Accounts](https://msdn.microsoft.com/en-us/library/bb646328\(v=office.15\)) collection for the session. GetAccountForFolder returns the [Account](https://msdn.microsoft.com/en-us/library/bb645103\(v=office.15\)) object if a match is found; otherwise, it returns a null reference.

In a Microsoft Outlook session that has multiple accounts defined in the profile, the folder that is displayed in the active explorer does not necessarily reside on the default store for that session; instead, it can reside on one of the multiple stores associated with the multiple accounts. This topic shows how to identify the account whose default delivery store is the same store that hosts the folder.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void DisplayAccountForCurrentFolder()
{
    Outlook.Folder myFolder = Application.ActiveExplorer().CurrentFolder 
        as Outlook.Folder;
    string msg = "Account for Current Folder:" + "\n" +
        GetAccountForFolder(myFolder).DisplayName;
    MessageBox.Show(msg,
        "GetAccountForFolder",
        MessageBoxButtons.OK,
        MessageBoxIcon.Information);
}

Outlook.Account GetAccountForFolder(Outlook.Folder folder)
{
    // Obtain the store on which the folder resides.
    Outlook.Store store = folder.Store;

    // Enumerate the accounts defined for the session.
    foreach (Outlook.Account account in Application.Session.Accounts)
    {
        // Match the DefaultStore.StoreID of the account
        // with the Store.StoreID for the currect folder.
        if (account.DeliveryStore.StoreID  == store.StoreID)
        {
            // Return the account whose default delivery store
            // matches the store of the given folder.
            return account;
        }
     }
     // No account matches, so return null.
     return null;
}
```

## See also



[Accounts](accounts.md)

