---
title: 'How to: Assign a Task to a Recipient'
TOCTitle: 'How to: Assign a Task to a Recipient'
ms:assetid: c6be97a7-de3f-43e5-9111-534d0f04e986
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184639(v=office.15)
ms:contentKeyID: 55119929
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Assign a Task to a Recipient

This example shows how to create a task and assign it to a recipient.

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


In the following code example, AssignTaskExample creates a [TaskItem](https://msdn.microsoft.com/en-us/library/bb624227\(v=office.15\)) object and specifies values for the [Subject](https://msdn.microsoft.com/en-us/library/bb624148\(v=office.15\)), [StartDate](https://msdn.microsoft.com/en-us/library/bb643988\(v=office.15\)), and [DueDate](https://msdn.microsoft.com/en-us/library/bb612307\(v=office.15\)) properties. The [Assign()](https://msdn.microsoft.com/en-us/library/bb644565\(v=office.15\)) method specifies that the task is an assigned task. After a [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) object is added to the TaskItem by using the [Add(String)](https://msdn.microsoft.com/en-us/library/bb612668\(v=office.15\)) method, the [Send()](https://msdn.microsoft.com/en-us/library/bb646608\(v=office.15\)) method sends the task to the recipient.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void AssignTaskExample()
{
    Outlook.TaskItem task = Application.CreateItem(
        Outlook.OlItemType.olTaskItem) as Outlook.TaskItem;
    task.Subject = "Tax Preparation";
    task.StartDate = DateTime.Parse("4/1/2007 8:00 AM");
    task.DueDate = DateTime.Parse("4/15/2007 8:00 AM");
    Outlook.RecurrencePattern pattern =
        task.GetRecurrencePattern();
    pattern.RecurrenceType = Outlook.OlRecurrenceType.olRecursYearly;
    pattern.PatternStartDate = DateTime.Parse("4/1/2007");
    pattern.NoEndDate = true;
    task.ReminderSet = true;
    task.ReminderTime = DateTime.Parse("4/1/2007 8:00 AM");
    task.Assign();
    task.Recipients.Add("accountant@example.com");
    task.Recipients.ResolveAll();
    task.Send();
}
```

## See also



[Tasks](tasks.md)

