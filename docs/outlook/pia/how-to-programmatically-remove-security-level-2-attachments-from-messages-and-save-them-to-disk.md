---
title: Programmatically remove security level 2 attachments from messages and save them to disk
TOCTitle: Programmatically remove security level 2 attachments from messages and save them to disk
ms:assetid: fb63e505-a243-40a5-919d-e4fe914af3f9
ms:mtpsurl: https://msdn.microsoft.com/library/Ff184657(v=office.15)
ms:contentKeyID: 55119822
ms.date: 07/24/2014
mtps_version: v=office.15
ms.localizationpriority: medium
---

# Programmatically remove security level 2 attachments from messages and save them to disk

This example shows how to remove security level 2 attachments from email messages and save them to a disk, from where they can be opened.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

Outlook protects users from malicious code transported via email attachments that have certain file extensions such as .exe or .bat. Those particular attachments are blocked by default and identified as Level 1 attachments. Level 2 attachments have a lesser chance of containing malicious code, but users cannot open a Level 2 attachment directly from an email message. A Level 2 attachment must first be saved to a disk.

By using the [SaveAsFile(String)](https://msdn.microsoft.com/library/bb624311\(v=office.15\)) method in the [Attachment](https://msdn.microsoft.com/library/bb609285\(v=office.15\)) object, you can save attachments to a disk. In the following code example, RemoveAttachmentsAndSaveToDisk first removes from mail items in a folder all Level 2 attachments that are greater than a specified size. This is done by enumerating the [Type](https://msdn.microsoft.com/library/bb609277\(v=office.15\)) property of each **Attachment** object in the [Attachments](https://msdn.microsoft.com/library/bb646211\(v=office.15\)) collection and removing the ones that are equal to [olByValue](https://msdn.microsoft.com/library/bb623448\(v=office.15\)). RemoveAttachmentsAndSaveToDisk then saves the removed attachment by using the **SaveAsFile** method.

> [!NOTE] 
> Collections in Outlook are linear. Use the [Index](/dotnet/api/microsoft.office.interop.outlook.attachment.index) operator to reference **Attachments**[1] to **Attachments**[n], where n represents the value of the [Count](/dotnet/api/microsoft.office.interop.outlook.attachments.count) property.
> 
> You cannot use a **foreach** statement to remove items in a collection. Instead, use an **Index** operator to obtain the first item in the collection, and then delete the item. Then use a **while** statement to determine when you have deleted the appropriate number of items in the collection. This will ensure that you have iterated over the correct number of items in the collection.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void RemoveAttachmentsAndSaveToDisk(string path,
    Outlook.Folder folder, int size)
{
    Outlook.Items attachItems;
    Outlook.Attachment attachment;
    Outlook.Attachments attachments;
    int byValueCount;
    int removeCount;
    bool saveMessage;
    try
    {
        // The restriction will find all items that
        // have attachments and MessageClass = IPM.Note.
        string filter = "@SQL=" + "\""
            + "urn:schemas:httpmail:hasattachment"
            + "\"" + " = True" + " AND " + "\""
            + "http://schemas.microsoft.com/mapi/proptag/0x001A001E"
            + "\"" + " = 'IPM.Note'";
        attachItems = folder.Items.Restrict(filter);
        foreach (Outlook.MailItem mail in attachItems)
        {
            saveMessage = false;
            byValueCount = 0;
            attachments = mail.Attachments;
            // Obtain the count of ByValue attachments.
            foreach (Outlook.Attachment attach in attachments)
            {
                if (attach.Size > size
                    & attach.Type ==
                    Outlook.OlAttachmentType.olByValue)
                {
                    byValueCount = byValueCount + 1;
                }
            }
            if (byValueCount > 0)
            {
                // removeCount is number of attachments to remove.
                removeCount = attachments.Count - byValueCount;
                while (mail.Attachments.Count != removeCount)
                {
                    // Use indexer to obtain 
                    // first attachment in collection.
                    attachment = mail.Attachments[1];
                    // You can refine this code to save 
                    // separate copies of attachments 
                    // with the same name.
                    attachment.SaveAsFile(path + @"\"
                        + attachment.FileName);
                    attachment.Delete();
                    if (saveMessage != true)
                    {
                        saveMessage = true;
                    }
                }
                if (saveMessage)
                {
                    mail.Save();
                }
            }
        }
    }
    catch (Exception ex)
    {
        Debug.WriteLine(ex.Message);
    }
}
```

## See also

- [Attachments](attachments.md)

