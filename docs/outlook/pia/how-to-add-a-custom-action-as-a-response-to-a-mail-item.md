﻿---
title: 'Add a Custom Action as a Response to a Mail Item'
TOCTitle: 'Add a Custom Action as a Response to a Mail Item'
ms:assetid: 99e8ba6b-9c47-4b10-968b-436b08d199ec
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424474(v=office.15)
ms:contentKeyID: 55119870
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Add a Custom Action as a Response to a Mail Item

This example shows how to add custom actions as a response to an e-mail item by using the [Add()](https://msdn.microsoft.com/en-us/library/bb612077\(v=office.15\)) method of the [Actions](https://msdn.microsoft.com/en-us/library/bb611963\(v=office.15\)) collection.

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


You can create custom actions programmatically to appear on the ribbon in the **Actions** group on the **Message** tab in an e-mail response. In the following code example, ReplyWithVoiceMail creates and adds a custom action named “Reply with Voice Mail” to the inspector command bar. ReplyWithVoiceMail first gets a [\_MailItem](https://msdn.microsoft.com/en-us/library/bb610623\(v=office.15\)) object and then creates an [Action](https://msdn.microsoft.com/en-us/library/bb646971\(v=office.15\)) object by calling the Add method of the Actions collection that is associated with the MailItem. It then sets the [Name](https://msdn.microsoft.com/en-us/library/bb624053\(v=office.15\)) property of the Action object to “Reply with Voice Mail”. The [ReplyStyle](https://msdn.microsoft.com/en-us/library/bb624278\(v=office.15\)), [ResponseStyle](https://msdn.microsoft.com/en-us/library/bb622491\(v=office.15\)), [CopyLike](https://msdn.microsoft.com/en-us/library/bb624213\(v=office.15\)), and [MessageClass](https://msdn.microsoft.com/en-us/library/bb624391\(v=office.15\)) properties are also set. Finally, the MailItem is saved.


> [!NOTE]
> <P>You can also add custom actions at design time by using the Outlook Forms Designer.</P>



If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

    private void ReplyWithVoiceMail()
    {
        Outlook.MailItem mail = (Outlook.MailItem)Application.ActiveInspector().CurrentItem;
        Outlook.Action action = mail.Actions.Add();
        action.Name = “Reply with Voice Mail”;
        action.ReplyStyle = Outlook.OlActionReplyStyle.olUserPreference;
        action.ResponseStyle = Outlook.OlActionResponseStyle.olOpen;
        action.CopyLike = Outlook.OlActionCopyLike.olReply;
        action.MessageClass = “IPM.Post.Voice Message”;
        mail.Save();
    }

## See also



[Mail](mail.md)
