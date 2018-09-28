---
title: 'Respond to a Task Request Item'
TOCTitle: 'Respond to a Task Request Item'
ms:assetid: 573c98ef-4d15-4fd1-bccd-25a22c9a63f0
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184608(v=office.15)
ms:contentKeyID: 55119896
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# Respond to a Task Request Item

This example shows how to get and respond to a task request item.

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


In the following code example, AcceptTaskRequest uses the [GetAssociatedTask(Boolean)](https://msdn.microsoft.com/en-us/library/bb645779\(v=office.15\)) method of the [TaskRequestItem](https://msdn.microsoft.com/en-us/library/bb610737\(v=office.15\)) object to get the [TaskItem](https://msdn.microsoft.com/en-us/library/bb624227\(v=office.15\)) object. The example then calls the [Respond(OlTaskResponse, Object, Object)](https://msdn.microsoft.com/en-us/library/bb644188\(v=office.15\)) method with the parameter set to [olTaskAccept](https://msdn.microsoft.com/en-us/library/bb624484\(v=office.15\)) to accept the task request.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void AcceptTaskRequest()
{
    string filter = "[MessageClass] = 'IPM.TaskRequest'";
    Outlook.Items items =
        Application.Session.GetDefaultFolder
        (Outlook.OlDefaultFolders.olFolderInbox).
        Items.Restrict(filter);
    if (items.Count > 0)
    {
        Outlook.TaskRequestItem taskRequest =
            (Outlook.TaskRequestItem)items[1];
        Outlook.TaskItem task =
            taskRequest.GetAssociatedTask(false);
        Outlook.TaskItem taskResponse = task.Respond(
            Outlook.OlTaskResponse.olTaskAccept, true, false);
        taskResponse.Send();
    }
}
```

## See also



[Tasks](tasks.md)

