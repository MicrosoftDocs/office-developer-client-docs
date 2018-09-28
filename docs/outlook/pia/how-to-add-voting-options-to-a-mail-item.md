---
title: 'Add Voting Options to a Mail Item'
TOCTitle: 'Add Voting Options to a Mail Item'
ms:assetid: 0fb209a8-178d-411e-9551-0a72e041fd65
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff424466(v=office.15)
ms:contentKeyID: 55119867
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Add Voting Options to a Mail Item

This example shows how to use the [VotingOptions](https://msdn.microsoft.com/en-us/library/bb652695\(v=office.15\)) property of the [MailItem](https://msdn.microsoft.com/en-us/library/bb643865\(v=office.15\)) object to add voting options to an email message.

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


Voting options on messages are used to give message recipients a list of choices and to track their responses. To create voting options programmatically, set a string that is a semicolon-delimited list of values for the VotingOptions property of a MailItem object. The values for the VotingOptions property will appear under the **Vote** command in the **Respond** group in the ribbon of the received message.

In the following example, OrderPizza creates voting options in a new mail message. OrderPizza first creates a MailItem, and then sets the VotingOptions property to “Cheese; Mushroom; Sausage; Combo; Veg Combo”, and the [Subject](https://msdn.microsoft.com/en-us/library/bb611353\(v=office.15\)) property to “Pizza Order”. When the “Pizza Order” message is sent, the voting options appear to recipients. For each response received, the recipient’s choice will be tallied on the **Tracking** page of the message in the sender’s Sent Items folder.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

    private void OrderPizza()
    {
        Outlook.MailItem mail = (Outlook.MailItem)Application.CreateItem(
            Outlook.OlItemType.olMailItem);
        mail.VotingOptions = “Cheese; Mushroom; Sausage; Combo; Veg Combo;”
        mail.Subject = “Pizza Order”;
        mail.Display(false);
    }

## See also



[Mail](mail.md)

