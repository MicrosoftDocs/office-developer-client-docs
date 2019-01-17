---
title: Search and obtain items in an aggregated view
TOCTitle: Search and obtain items in an aggregated view
ms:assetid: 1a875dc8-dd52-4e9c-b292-5f6ba3d7a940
ms:mtpsurl: https://msdn.microsoft.com/library/Ff184592(v=office.15)
ms:contentKeyID: 55119925
ms.date: 07/24/2014
mtps_version: v=office.15
localization_priority: Normal
---

# Search and obtain items in an aggregated view

This example shows how to search for items in multiple folders and stores and to return those items in an aggregated table view.

## Example

The [GetTable()](https://msdn.microsoft.com/library/ff184699\(v=office.15\)) method of the [TableView](https://msdn.microsoft.com/library/bb608854\(v=office.15\)) object can return, in an aggregated view, a [Table](https://msdn.microsoft.com/library/bb652856\(v=office.15\)) object that contains items from one or more folders in the same store or spanning over multiple stores. This is particularly useful when you want to access items returned from a search (for example, a search on all mail items in a store). This topic shows an example of how to use **Instant Search** to search for all items received from the manager of the current user that are marked important, and then display the subject of each search result.

In the following code example, the **GetItemsInView** method checks whether the current user’s primary delivery store account is an Exchange account, whether the current user has a manager, and whether **Instant Search** is operational in the default store of the session. Because the search relies on the [Search](https://msdn.microsoft.com/library/bb610561\(v=office.15\)) method of the [Explorer](https://msdn.microsoft.com/library/bb623678\(v=office.15\)) object, and the search result is obtained by using the **GetTable** method, **GetItemsInView** creates an **Explorer** object, displays the Inbox in this object, and uses it to set up the search. 

**GetItemsInView** searches all folders of the [MailItem](https://msdn.microsoft.com/library/bb643865\(v=office.15\)) type for items from the current user's manager that are marked as important. After **GetItemsInView** calls the [Search](https://msdn.microsoft.com/library/bb610561\(v=office.15\)) method, any search results are displayed in the Explorer, including items from other folders and stores that meet the search criteria. **GetItemsInView** gets a **TableView** object that contains this explorer view of the search results. By using the **GetTable** method of this **TableView** object, **GetItemsInView** then gets a **Table** object that contains the aggregated items returned from the search. Finally **GetItemsInView** displays the subject column of each row of the **Table** object that represents an item in the search results.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void GetItemsInView()
{
    Outlook.AddressEntry currentUser =
        Application.Session.CurrentUser.AddressEntry;

    // Check whether the current user uses the Exchange Server.
    if (currentUser.Type == "EX")
    {
        Outlook.ExchangeUser manager =
            currentUser.GetExchangeUser().GetExchangeUserManager();

        // Check whether the current user has a manager.
        if (manager != null)
        {
            string managerName = manager.Name;

            // Check whether Instant Search is enabled and 
            // operational in the default store.
            if (Application.Session.DefaultStore.IsInstantSearchEnabled)
            {
                Outlook.Folder inbox =
                    Application.Session.GetDefaultFolder(
                    Outlook.OlDefaultFolders.olFolderInbox);

                // Create a new explorer to display the Inbox as
                // the current folder.
                Outlook.Explorer explorer =
                    Application.Explorers.Add(inbox,
                    Outlook.OlFolderDisplayMode.olFolderDisplayNormal);

                // Make the new explorer visible.
                explorer.Display;

                // Search for items from the manager marked important, 
                // from all folders of the same item type as the current folder, 
                // which is the MailItem item type.
                string searchFor =
                    "from:" + "\"" + managerName 
                    + "\"" + " importance:high";
                explorer.Search(searchFor,
                    Outlook.OlSearchScope.olSearchScopeAllFolders);

                // Any search results are displayed in that new explorer
                // in an aggregated table view.
                Outlook.TableView tableView = 
                    explorer.CurrentView as Outlook.TableView;

                // Use GetTable of that table view to obtain items in that
                // aggregated view in a Table object.
                Outlook.Table table = tableView.GetTable();
                while (!table.EndOfTable)
                {
                    // Then display each row in the Table object
                    // that represents an item in the search results.
                    Outlook.Row nextRow = table.GetNextRow();
                    Debug.WriteLine(nextRow["Subject"]);
                }
            }
        }
    }
}
```

## See also

- [Search and filter](search-and-filter.md)

