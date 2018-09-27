---
title: 'How to: Programmatically Remove Security Level 2 Attachments from Messages and Save Them to Disk'
TOCTitle: 'How to: Programmatically Remove Security Level 2 Attachments from Messages and Save Them to Disk'
ms:assetid: fb63e505-a243-40a5-919d-e4fe914af3f9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184657(v=office.15)
ms:contentKeyID: 55119822
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Programmatically Remove Security Level 2 Attachments from Messages and Save Them to Disk

This example shows how to remove security Level 2 attachments from e-mail messages and save them to a disk, from where they can be opened.

## Example

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>The following code example is an excerpt from <em>Programming Applications for Microsoft Office Outlook 2007</em>, from <a href="http://www.microsoft.com/learning/books/default.mspx">Microsoft Press</a> (ISBN 9780735622494, copyright Microsoft Press 2007, all rights reserved).</p>
<p><a href="http://www.amazon.com/gp/product/0735622493?ie=utf8%26tag=msmsdn-20%26linkcode=as2%26camp=1789%26creative=9325%26creativeasin=0735622493">Buy this book</a></p>
<p><a href="https://msdn.microsoft.com/en-us/library/cc513844(v=office.15)">Sample chapters</a></p></td>
</tr>
</tbody>
</table>


Outlook protects users from malicious code transported via e-mail attachments that have certain file extensions such as .exe or .bat. Those particular attachments are blocked by default and identified as Level 1 attachments. Level 2 attachments have a lesser chance of containing malicious code, but users cannot open a Level 2 attachment directly from an e-mail message. A Level 2 attachment must first be saved to a disk.

By using the [SaveAsFile(String)](https://msdn.microsoft.com/en-us/library/bb624311\(v=office.15\)) method in the [Attachment](https://msdn.microsoft.com/en-us/library/bb609285\(v=office.15\)) object, you can save attachments to a disk. In the following code example, RemoveAttachmentsAndSaveToDisk first removes from mail items in a folder all Level 2 attachments that are greater than a specified size. This is done by enumerating the [Type](https://msdn.microsoft.com/en-us/library/bb609277\(v=office.15\)) property of each Attachment object in the [Attachments](https://msdn.microsoft.com/en-us/library/bb646211\(v=office.15\)) collection and removing the ones that are equal to [olByValue](https://msdn.microsoft.com/en-us/library/bb623448\(v=office.15\)). RemoveAttachmentsAndSaveToDisk then saves the removed attachment by using the SaveAsFile method.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>C# note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Collections in Outlook are linear. Use the <a href="https://msdn.microsoft.com/en-us/library/bb608897(v=office.15)">Index</a>[n] operator to reference Attachments[1] to Attachments[n] where n represents the value of the <a href="https://msdn.microsoft.com/en-us/library/bb610960(v=office.15)">Count</a> property.</p>
<p>You cannot use a foreach statement to remove items in a collection. Instead, use an Index operator to obtain the first item in the collection, and then delete the item. Then use a while statement to determine when you have deleted the appropriate number of items in the collection. This will ensure that you have iterated over the correct number of items in the collection.</p></td>
</tr>
</tbody>
</table>


If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
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

#### Other resources

[Attachments](attachments.md)

