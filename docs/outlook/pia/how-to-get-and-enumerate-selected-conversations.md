---
title: Get and enumerate selected conversations
TOCTitle: Get and enumerate selected conversations
ms:assetid: 835312ea-2b29-49a5-b128-f69cf8d4427c
ms:mtpsurl: https://msdn.microsoft.com/library/Ff184621(v=office.15)
ms:contentKeyID: 55119833
ms.date: 07/24/2014
mtps_version: v=office.15
localization_priority: Normal
---

# Get and enumerate selected conversations

This example obtains and enumerates selected conversations by using the [GetSelection(OlSelectionContents)](https://msdn.microsoft.com/library/ff185002\(v=office.15\)) method.

## Example

Microsoft Outlook can be set to display items in the Inbox by conversation. If a user makes a selection in the Inbox, you can obtain the selection programmatically, including conversation headers and conversation items. The code example in this topic shows how to obtain a selection in the Inbox and enumerate the mail items in each conversation in the selection.

The example contains one method, DemoConversationHeadersFromSelection. The method sets the current view to the Inbox, and then checks whether the current view is a table view that displays conversations sorted by date. To obtain a selection, including any selected [ConversationHeader](https://msdn.microsoft.com/library/ff184727\(v=office.15\)) objects, DemoConversationHeadersFromSelection uses the **GetSelection** method of the [Selection](https://msdn.microsoft.com/library/bb612099\(v=office.15\)) object, specifying the [olConversationHeaders](https://msdn.microsoft.com/library/ff184867\(v=office.15\)) constant as an argument. If conversation headers are selected, DemoConversationHeadersFromSelection uses the [SimpleItems](https://msdn.microsoft.com/library/ff184992\(v=office.15\)) object to enumerate items in each selected conversation, and then displays the subject of those conversation items that are [MailItem](https://msdn.microsoft.com/library/bb643865\(v=office.15\)) objects.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void DemoConversationHeadersFromSelection()
{
    // Obtain Inbox.
    Outlook.Folder inbox =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox)
        as Outlook.Folder;
    // Set ActiveExplorer.CurrentFolder to Inbox.
    // Inbox must be current folder.
    Application.ActiveExplorer().CurrentFolder = inbox;
    // Ensure that current view is TableView.
    if (inbox.CurrentView.ViewType ==
        Outlook.OlViewType.olTableView)
    {
        Outlook.TableView view =
            inbox.CurrentView as Outlook.TableView;
        if (view.ShowConversationByDate == true)
        {
            Outlook.Selection selection =
                Application.ActiveExplorer().Selection;
            Debug.WriteLine("Selection.Count = " + selection.Count);
            // Call GetSelection to create a Selection object
            // that contains ConversationHeader objects.
            Outlook.Selection convHeaders =
                selection.GetSelection(
                Outlook.OlSelectionContents.olConversationHeaders)
                as Outlook.Selection;
            Debug.WriteLine("Selection.Count (ConversationHeaders) = " 
                + convHeaders.Count);
            if (convHeaders.Count >= 1)
            {
                foreach (Outlook.ConversationHeader convHeader in convHeaders)
                {
                    // Enumerate the items in the ConversationHeader.
                    Outlook.SimpleItems items = convHeader.GetItems();
                    for (int i = 1; i <= items.Count; i++)
                    {
                        // Enumerate only MailItems in this example.
                        if (items[i] is Outlook.MailItem)
                        {
                            Outlook.MailItem mail = 
                                items[i] as Outlook.MailItem;
                            Debug.WriteLine(mail.Subject 
                                + " Received:" + mail.ReceivedTime);
                        }
                    }
                }
            }
        }
    }
}
```

## See also

- [Conversations](conversations.md)

