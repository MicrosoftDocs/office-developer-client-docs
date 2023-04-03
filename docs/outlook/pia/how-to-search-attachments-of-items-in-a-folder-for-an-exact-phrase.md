---
title: Search attachments of items in a folder for an exact phrase
TOCTitle: Search attachments of items in a folder for an exact phrase
ms:assetid: 3202c0c7-ee3d-4396-b3a9-d24990b44829
ms:mtpsurl: https://learn.microsoft.com/office/client-developer/outlook/pia/how-to-search-attachments-of-items-in-a-folder-for-an-exact-phrase
ms:contentKeyID: 55119889
ms.date: 09/14/2021
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Search attachments of items in a folder for an exact phrase

This example searches for the exact search string "office" in attachments to items in the Inbox.

## Example

This code sample uses a DAV Searching and Locating (DASL) syntax to specify a query. To construct the filter, the code sample first checks whether Instant Search is enabled in the default store to determine whether to use the **ci\_phrasematch** keyword for an exact phrase match to "office" in any attachment. The sample then applies the filter to the [GetTable](/dotnet/api/microsoft.office.interop.outlook.mapifolder.gettable) method on the Inbox and obtains the results in a [Table](/dotnet/api/microsoft.office.interop.outlook.table) object. The code sample then displays the subject of each of the returned items in the **Table**.

The code sample specifies the **Attachments** property of an item using the namespace representation, `https://schemas.microsoft.com/mapi/proptag/0x0EA5001E`. The syntax for using the **ci\_phrasematch** keyword is:

`<PropertySchemaName> ci_phrasematch <ComparisonString>`

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **Imports** or **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

```vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```vb
Private Sub DemoSearchAttachments()
    Dim filter As String
    Const PR_SEARCH_ATTACHMENTS As String = _
        "http://schemas.microsoft.com/mapi/proptag/0x0EA5001E"
    If (Application.Session.DefaultStore.IsInstantSearchEnabled) Then
        filter = "@SQL=" & Chr(34) _
            & PR_SEARCH_ATTACHMENTS & Chr(34) _
            & " ci_phrasematch 'office'"
        Dim table As Outlook.Table = _
            Application.Session.GetDefaultFolder( _
            Outlook.OlDefaultFolders.olFolderInbox).GetTable( _
            filter, Outlook.OlTableContents.olUserItems)
        While Not (table.EndOfTable)
            Dim row As Outlook.Row = table.GetNextRow()
            Debug.WriteLine(row("Subject"))
        End While
    End If
End Sub
```

```csharp
private void DemoSearchAttachments()
{
    string filter;
    const string PR_SEARCH_ATTACHMENTS =
        "http://schemas.microsoft.com/mapi/proptag/0x0EA5001E";
    if (Application.Session.DefaultStore.IsInstantSearchEnabled)
    {
        filter = "@SQL=" + "\""
            + PR_SEARCH_ATTACHMENTS + "\""
            + " ci_phrasematch 'office'";
        Outlook.Table table = Application.Session.GetDefaultFolder(
            Outlook.OlDefaultFolders.olFolderInbox).GetTable(
            filter, Outlook.OlTableContents.olUserItems);
        while (!table.EndOfTable)
        {
            Outlook.Row row = table.GetNextRow();
            Debug.WriteLine(row["Subject"]);
        }
    }
}
```

## See also

- [Search and filter](search-and-filter.md)
