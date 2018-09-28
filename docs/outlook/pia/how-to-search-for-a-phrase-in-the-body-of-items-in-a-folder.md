---
title: 'Search for a Phrase in the Body of Items in a Folder'
TOCTitle: 'Search for a Phrase in the Body of Items in a Folder'
ms:assetid: 2c9f3b5f-ed91-4a07-b247-8f89f00cbc68
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb644806(v=office.15)
ms:contentKeyID: 55119924
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Search for a Phrase in the Body of Items in a Folder

This example searches for the string "office" in the Body of items in the Inbox.

## Example

This code sample uses a DAV Searching and Locating (DASL) syntax to specify a query. To construct the filter, the code sample first checks if Instant Search is enabled in the default store to determine whether to use the ci\_phrasematch keyword for an exact phrase match of "office" in the item body, or the like keyword to match any occurrence of "office" as an exact string or a substring in the item body. The sample then applies the filter to the [GetTable](https://msdn.microsoft.com/en-us/library/bb612592\(v=office.15\)) method on the Inbox and obtains the results in a [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object. The code sample then displays the subject of each of the returned items in the Table.

The code sample specifies the Body property by using the namespace representation urn:schemas:httpmail:textdescription.

The syntax for using the ci\_phrasematch keyword is:

\<PropertySchemaName\> ci\_phrasematch \<ComparisonString\>

The syntax for using the like keyword for prefix matching is:

\<PropertySchemaName\> like \<Token\>%

The syntax for using the like keyword for any substring matching is:

\<PropertySchemaName\> like %\<Token\>%

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The Imports or using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

``` vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` vb
Private Sub DemoSearchBody()
    Dim filter As String
    If (Application.Session.DefaultStore.IsInstantSearchEnabled) Then
        filter = "@SQL=" & Chr(34) _
            & "urn:schemas:httpmail:textdescription" & Chr(34) _
            & " ci_phrasematch 'office'"
    Else
        filter = "@SQL=" & Chr(34) _
            & "urn:schemas:httpmail:textdescription" & Chr(34) _
            & " like '%office%'"
    End If
    Dim table As Outlook.Table = _
        Application.Session.GetDefaultFolder( _
        Outlook.OlDefaultFolders.olFolderInbox).GetTable( _
        filter, Outlook.OlTableContents.olUserItems)
    While Not (table.EndOfTable)
        Dim row As Outlook.Row = table.GetNextRow()
        Debug.WriteLine(row("Subject"))
    End While
End Sub
```

``` csharp
private void DemoSearchBody()
{
    string filter;
    if (Application.Session.DefaultStore.IsInstantSearchEnabled)
    {
        filter = "@SQL=" + "\""
            + "urn:schemas:httpmail:textdescription" + "\""
            + " ci_phrasematch 'office'";
    }
    else
    {
        filter = "@SQL=" + "\""
            + "urn:schemas:httpmail:textdescription" + "\""
            + " like '%office%'";
    }
    Outlook.Table table = Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox).GetTable(
        filter, Outlook.OlTableContents.olUserItems);
    while (!table.EndOfTable)
    {
        Outlook.Row row = table.GetNextRow();
        Debug.WriteLine(row["Subject"]);
    }
}
```

## See also



[Search and Filter](search-and-filter.md)

