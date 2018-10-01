---
title: 'Specify Different Recipient Types for a Mail Item'
TOCTitle: 'Specify Different Recipient Types for a Mail Item'
ms:assetid: 2a3ace9f-627c-4fdd-b182-afc1b53af85b
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184598(v=office.15)
ms:contentKeyID: 55119871
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Specify Different Recipient Types for a Mail Item

This example shows how to programmatically set different recipient types (To, Cc, or Bcc) for a mail item.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

The following code example illustrates how to specify whether a recipient of a [MailItem](https://msdn.microsoft.com/en-us/library/bb643865\(v=office.15\)) object is a To, Cc, or Bcc recipient. SetRecipientTypeForMail creates a **MailItem** object, adds three [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) objects to the [Recipients](https://msdn.microsoft.com/en-us/library/bb646361\(v=office.15\)) collection of the MailItem, and then sets the [Type](https://msdn.microsoft.com/en-us/library/bb611841\(v=office.15\)) property of each **Recipient** object to a value from the [OlMailRecipientType](https://msdn.microsoft.com/en-us/library/bb647641\(v=office.15\)) enumeration.


> [!NOTE]
> <P>The Type property of the **Recipient** object is an int type and does not correlate to a specific recipient type enumeration.</P>



If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void SetRecipientTypeForMail()
{
    Outlook.MailItem mail = Application.CreateItem(
        Outlook.OlItemType.olMailItem) as Outlook.MailItem;
    mail.Subject = "Sample Message";
    Outlook.Recipient recipTo =
        mail.Recipients.Add("someone@example.com");
    recipTo.Type = (int)Outlook.OlMailRecipientType.olTo;
    Outlook.Recipient recipCc =
        mail.Recipients.Add("someonecc@example.com");
    recipCc.Type = (int)Outlook.OlMailRecipientType.olCC;
    Outlook.Recipient recipBcc =
        mail.Recipients.Add("someonebcc@example.com");
    recipBcc.Type = (int)Outlook.OlMailRecipientType.olBCC;
    mail.Recipients.ResolveAll();
    mail.Display(false);
}
```

## See also



[Mail](mail.md)

