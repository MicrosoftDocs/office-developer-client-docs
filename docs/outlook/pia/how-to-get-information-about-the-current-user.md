---
title: 'How to: Get Information About the Current User'
TOCTitle: 'How to: Get Information About the Current User'
ms:assetid: 3802523a-3ccf-4cca-a348-abe2645a0d9c
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184601(v=office.15)
ms:contentKeyID: 55119840
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- csharp
---

# How to: Get Information About the Current User

This example shows how to get the current user’s information, such as name, job title, and telephone number.

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


To obtain an [ExchangeUser](https://msdn.microsoft.com/en-us/library/bb609574\(v=office.15\)) object from an [AddressEntry](https://msdn.microsoft.com/en-us/library/bb609728\(v=office.15\)) object, call the [GetExchangeUser()](https://msdn.microsoft.com/en-us/library/bb611808\(v=office.15\)) method on the AddressEntry object. In the following procedure, GetCurrentUserInfo gets the [AddressEntry](https://msdn.microsoft.com/en-us/library/bb644359\(v=office.15\)) property for the [Recipient](https://msdn.microsoft.com/en-us/library/bb624370\(v=office.15\)) object by using the [CurrentUser](https://msdn.microsoft.com/en-us/library/bb622574\(v=office.15\)) property. If the AddressEntry object represents an Exchange mailbox user, GetCurrentUserInfo calls the GetExchangeUser method and an ExchangeUser object is returned. The [Name](https://msdn.microsoft.com/en-us/library/bb622941\(v=office.15\)), [PrimarySmtpAddress](https://msdn.microsoft.com/en-us/library/bb645506\(v=office.15\)), [JobTitle](https://msdn.microsoft.com/en-us/library/bb645451\(v=office.15\)), [Department](https://msdn.microsoft.com/en-us/library/bb623789\(v=office.15\)), [OfficeLocation](https://msdn.microsoft.com/en-us/library/bb611429\(v=office.15\)), [BusinessTelephoneNumber](https://msdn.microsoft.com/en-us/library/bb612294\(v=office.15\)), and [MobileTelephoneNumber](https://msdn.microsoft.com/en-us/library/bb609292\(v=office.15\)) properties are written to the trace listeners of the [Listeners](http://msdn.microsoft.com/en-us/library/system.diagnostics.debug.listeners.aspx) collection.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` csharp
private void GetCurrentUserInfo()
{
    Outlook.AddressEntry addrEntry =
        Application.Session.CurrentUser.AddressEntry;
    if (addrEntry.Type == "EX")
    {
        Outlook.ExchangeUser currentUser =
            Application.Session.CurrentUser.
            AddressEntry.GetExchangeUser();
        if (currentUser != null)
        {
            StringBuilder sb = new StringBuilder();
            sb.AppendLine("Name: "
                + currentUser.Name);
            sb.AppendLine("STMP address: "
                + currentUser.PrimarySmtpAddress);
            sb.AppendLine("Title: "
                + currentUser.JobTitle);
            sb.AppendLine("Department: "
                + currentUser.Department);
            sb.AppendLine("Location: "
                + currentUser.OfficeLocation);
            sb.AppendLine("Business phone: "
                + currentUser.BusinessTelephoneNumber);
            sb.AppendLine("Mobile phone: "
                + currentUser.MobileTelephoneNumber);
            Debug.WriteLine(sb.ToString());
        }
    }
}
```

## See also

#### Other resources

[Exchange Users](exchange-users.md)

