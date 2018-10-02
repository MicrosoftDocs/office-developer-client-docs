---
title: Synchronize Outlook with a SharePoint folder
TOCTitle: Synchronize Outlook with a SharePoint folder
ms:assetid: fecb04ab-39c6-43e1-9a21-12ecb29d94fb
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424483(v=office.15)
ms:contentKeyID: 55119853
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Synchronize Outlook with a SharePoint folder

This example shows how to programmatically connect Outlook with a SharePoint folder and to synchronize the folder contents.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

In Outlook, you can synchronize calendars, contact lists, task lists, discussion boards, and document libraries to SharePoint folders. Based on the URL provided upon synchronization, Outlook will create a new folder of the same base type as the SharePoint folder. For example, synchronizing to a SharePoint calendar folder will create a new calendar folder in Outlook. SharePoint synchronization folders are stored in their own Outlook Personal Folders (.pst) file outside of the user’s mailbox. You can connect to a SharePoint folder by using the [OpenSharedFolder(String, Object, Object, Object)](https://msdn.microsoft.com/en-us/library/bb610157\(v=office.15\)) method of the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object. Note that you must use a stssync:// URL that provides details about the SharePoint server, folder path, and other information that Outlook needs to open a SharePoint folder.

When connecting to a SharePoint folder programmatically, you must determine the proper URL to use to create the sharing relationship. Because the stssync:// URL is not provided in the SharePoint user interface for the folder, manually link the destination folder into Outlook. Then use the first procedure, DisplaySharePointUrl, in the following code example, to get the correct URL. DisplaySharePointUrl uses the [Table](https://msdn.microsoft.com/en-us/library/bb652856\(v=office.15\)) object to look for the sharing binding information in the current folder for the active explorer window. If one or more binding contexts are found, the URLs for all available sharing contexts will be displayed.

Now you have the proper URL to create the sharing relationship. To synchronize the new SharePoint folder in Outlook, copy and paste the URL to the assignment of the string variable calendarUrl in the second procedure, AddSpsFolder. AddSpsFolder automates the synchronization of the new SharePoint folder in Outlook by using the **NameSpace.OpenSharedFolder** method with a `stssync://` URL (in this case, the URL produced by the DisplaySharePointUrl procedure). AddSpsFolderalso provides a custom folder name, “Example SPS Calendar”, and specifies Outlook to use the default Time to Live (TTL) for the folder. SharePoint folders always download item attachments, so you do not have to specify that here.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void DisplaySharePointUrl()
{
    const string PROP_SYNC_URL = 
        "http://schemas.microsoft.com/mapi/id/{00062040-0000-0000-C000-000000000046}/8A24001E";

    Outlook.Folder folder = Application.ActiveExplorer().CurrentFolder as Outlook.Folder;
    Outlook.Table table = folder.GetTable(Type.Missing, Outlook.OlTableContents.olHiddenItems);
    table.Columns.RemoveAll();
    table.Columns.Add("MessageClass");
    table.Columns.Add(PROP_SYNC_URL);

    StringBuilder sb = new StringBuilder();
    while (!table.EndOfTable)
    {
        Outlook.Row row = table.GetNextRow();
        string msgClass, spsUrl;
        msgClass = row["MessageClass"] as string;
        spsUrl = row[PROP_SYNC_URL] as string;

        if (msgClass == "IPM.Sharing.Binding.In")
        {
            sb.Append(spsUrl);
            sb.Append("\r\n");
        }
    }
    if (sb.Length > 0)
    {
        System.Windows.Forms.MessageBox.Show(
            "The following SharePoint Folder URLs were found:\r\n" + sb.ToString());
    }
    else
    {
        System.Windows.Forms.MessageBox.Show("No SharePoint URLs were found in this folder.");
    }
}

private void AddSpsFolder()
{
    string calendarUrl = "stssync://sts/?ver=1.1&type=calendar&cmd=add-folder&base-url=
        http://example.org/calendar&list-url=/Lists/Calendar/calendar.aspx&guid=&site-name=
        Example%20Site&list-name=Calendar";
    string folderName = "Example SPS Calendar";
    bool useDefaultTTL = true;
    Outlook.Folder calendarFolder =
        Application.Session.OpenSharedFolder(calendarUrl, folderName, Type.Missing, useDefaultTTL) 
        as Outlook.Folder;
    Outlook.Explorer exp =
        Application.Explorers.Add(calendarFolder, Outlook.OlFolderDisplayMode.olFolderDisplayNormal);
    exp.Display();
}
```

## See also

- [Group sharing](group-sharing.md)

