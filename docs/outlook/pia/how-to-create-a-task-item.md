---
title: Create a task item
TOCTitle: Create a task item
ms:assetid: d458dd31-2771-4a3c-a713-13c7e4e02a74
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184644(v=office.15)
ms:contentKeyID: 55119894
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Create a task item

This example shows how to create a task item by using the [MarkAsTask(OlMarkInterval)](https://msdn.microsoft.com/en-us/library/bb609068\(v=office.15\)) method.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).


In the following code example, CreateToDoItemExample creates a to-do item by calling the **MarkAsTask** method on the item and then saving the item. The example marks the item for follow-up tomorrow and sets a reminder for tomorrow at 10:00 A.M. by using the [ReminderSet](https://msdn.microsoft.com/en-us/library/bb622600\(v=office.15\)) and [ReminderTime](https://msdn.microsoft.com/en-us/library/bb622803\(v=office.15\)) properties. The example then uses the [Save()](https://msdn.microsoft.com/en-us/library/bb645518\(v=office.15\)) method to save the item.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```


```csharp
private void CreateToDoItemExample()
{
    // Date operations
    DateTime today = DateTime.Parse("10:00 AM");
    TimeSpan duration = TimeSpan.FromDays(1);
    DateTime tomorrow = today.Add(duration);
    Outlook.MailItem mail = Application.Session.
        GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderInbox).Items.Find(
        "[MessageClass]='IPM.Note'") as Outlook.MailItem;
    mail.MarkAsTask(Outlook.OlMarkInterval.olMarkTomorrow);
    mail.TaskStartDate = today;
    mail.ReminderSet = true;
    mail.ReminderTime = tomorrow;
    mail.Save();
}
```

## See also

- [Tasks](tasks.md)

