---
title: Display the address lists for a profile
TOCTitle: Display the address lists for a profile
ms:assetid: ced8230b-110b-4ccb-a699-588798144154
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184643(v=office.15)
ms:contentKeyID: 55119802
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Display the address lists for a profile

This example shows how to display the address lists for the current profile.

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


The current profile contains address lists that are represented by the [AddressLists](https://msdn.microsoft.com/en-us/library/bb611894\(v=office.15\)) collection. To get an instance of the AddressLists collection, you must use the [AddressLists](https://msdn.microsoft.com/en-us/library/bb624048\(v=office.15\)) property of the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object.

In the following code example, EnumerateAddressLists first enumerates each [AddressList](https://msdn.microsoft.com/en-us/library/bb623538\(v=office.15\)) object in the AddressLists collection by using a foreach statement. The example then creates a string that contains the values of the [Name](https://msdn.microsoft.com/en-us/library/bb609849\(v=office.15\)), [ResolutionOrder](https://msdn.microsoft.com/en-us/library/bb646853\(v=office.15\)), [IsReadOnly](https://msdn.microsoft.com/en-us/library/bb612676\(v=office.15\)), and [IsInitialAddressList](https://msdn.microsoft.com/en-us/library/bb646646\(v=office.15\)) properties. Finally, EnumerateAddressLists writes the string to the trace listeners of the [Listeners](http://msdn.microsoft.com/en-us/library/system.diagnostics.debug.listeners.aspx) collection. This displays each address list for the current profile.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void EnumerateAddressLists()
{
    Outlook.AddressLists addrLists =
         Application.Session.AddressLists;
    foreach (Outlook.AddressList addrList in addrLists)
    {
        StringBuilder sb = new StringBuilder();
        sb.AppendLine("Display Name: " + addrList.Name);
        sb.AppendLine("Resolution Order: "
            + addrList.ResolutionOrder.ToString());
        sb.AppendLine("Read-only : "
            + addrList.IsReadOnly.ToString());
        sb.AppendLine("Initial Address List: "
            + addrList.IsInitialAddressList.ToString());
        sb.AppendLine("");
        Debug.WriteLine(sb.ToString());
    }
}
```

## See also

- [Address book](address-book.md)

