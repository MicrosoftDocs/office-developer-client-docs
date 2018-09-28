---
title: 'Get the Default Message Class of a Folder'
TOCTitle: 'Get the Default Message Class of a Folder'
ms:assetid: 1c5faefd-b180-4114-a955-3fc524210317
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184594(v=office.15)
ms:contentKeyID: 55119860
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Get the Default Message Class of a Folder

This example shows how to use the [DefaultMessageClass](https://msdn.microsoft.com/en-us/library/bb646541\(v=office.15\)) property to obtain the default message class of a folder.

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


To obtain the default message class for a folder, use the DefaultMessageClass property of the [MAPIFolder](https://msdn.microsoft.com/en-us/library/bb624369\(v=office.15\)) object. For example, a [Folder](https://msdn.microsoft.com/en-us/library/bb645774\(v=office.15\)) object that has a DefaultMessageClass of IPM.Contact means that it represents a Contact folder. However, if the folder has a custom form or a replacement form as a default form, you must use the [PropertyAccessor](https://msdn.microsoft.com/en-us/library/bb646034\(v=office.15\)) object to determine the message class of the default form. The DefaultMessageClass property does not return the message class of the default form for the folder.

In the following code example, the GetDefaultMessageClass procedure uses the PropertyAccessor to determine the default form of a folder. If the folder property PR\_DEF\_POST\_MSGCLASS [(PidTagDefaultPostMessageClass)](https://msdn.microsoft.com/en-us/library/cc815305\(v=office.15\)) is not found and Outlook raises an error, the try…catch block returns the DefaultMessageClass property for the Folder.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private string GetDefaultMessageClass(Outlook.Folder folder)
{
    if (folder == null)
        throw new ArgumentNullException();
    try
    {
        const string PR_DEF_POST_MSGCLASS =
            @"http://schemas.microsoft.com/mapi/proptag/0x36E5001E";
        string messageClass =
            folder.PropertyAccessor.GetProperty(
            PR_DEF_POST_MSGCLASS).ToString();
        return messageClass;
    }
    catch
    {
        return folder.DefaultMessageClass;
    }
}
```

## See also



[Folders](folders.md)

