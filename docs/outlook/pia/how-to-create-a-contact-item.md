---
title: 'Create a Contact Item'
TOCTitle: 'Create a Contact Item'
ms:assetid: b316294a-7f70-4e54-9375-4dc515e9fd11
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184633(v=office.15)
ms:contentKeyID: 55119823
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Create a Contact Item

This example shows how to create a contact item and set various properties for the contact.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).


An Outlook[ContactItem](https://msdn.microsoft.com/en-us/library/bb644956\(v=office.15\)) object has more than 100 built-in properties such as [Department](https://msdn.microsoft.com/en-us/library/bb610564\(v=office.15\)), [CompanyName](https://msdn.microsoft.com/en-us/library/bb610212\(v=office.15\)), [OfficeLocation](https://msdn.microsoft.com/en-us/library/bb647145\(v=office.15\)), and [JobTitle](https://msdn.microsoft.com/en-us/library/bb609294\(v=office.15\)). You can add custom properties, if a built-in property is not available, by using the [UserProperties](https://msdn.microsoft.com/en-us/library/bb611428\(v=office.15\)) collection. Once you create a ContactItem, you can set its properties.

In the following code example, CreateContactExample creates a ContactItem and sets commonly used properties for that object. It then calls the [ShowCheckPhoneDialog(OlContactPhoneNumber)](https://msdn.microsoft.com/en-us/library/bb646168\(v=office.15\)) method on the ContactItem object. The ShowCheckPhoneDialog method allows the user to resolve a phone number based on local dialing conventions.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void CreateContactExample()
{
    Outlook.ContactItem contact = Application.CreateItem(
        Outlook.OlItemType.olContactItem) as Outlook.ContactItem;
    contact.FirstName = "Mellissa";
    contact.LastName = "MacBeth";
    contact.JobTitle = "Account Representative";
    contact.CompanyName = "Contoso Ltd.";
    contact.OfficeLocation = "36/2529";
    contact.BusinessTelephoneNumber = "4255551212 x432";
    contact.WebPage = "http://www.contoso.com";
    contact.BusinessAddressStreet = "1 Microsoft Way";
    contact.BusinessAddressCity = "Redmond";
    contact.BusinessAddressState = "WA";
    contact.BusinessAddressPostalCode = "98052";
    contact.BusinessAddressCountry =
        "United States of America";
    contact.Email1Address = "melissa@contoso.com";
    contact.Email1AddressType = "SMTP";
    contact.Email1DisplayName =
        "Melissa MacBeth (mellissa@contoso.com)";
    contact.Display(false);
    contact.ShowCheckPhoneDialog(
        Outlook.OlContactPhoneNumber.
        olContactPhoneBusiness);
}
```

## See also



[Contacts](contacts.md)

