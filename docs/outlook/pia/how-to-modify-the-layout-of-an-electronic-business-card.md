---
title: 'Modify the Layout of an Electronic Business Card'
TOCTitle: 'Modify the Layout of an Electronic Business Card'
ms:assetid: f387c4a7-59c5-4b6a-b33a-1bfa7d499bbf
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff184653(v=office.15)
ms:contentKeyID: 55119838
ms.date: 07/24/2014
mtps_version: v=office.15


---

# Modify the Layout of an Electronic Business Card

This example shows how to modify the layout of an Electronic Business Card by using the [BusinessCardLayoutXml](https://msdn.microsoft.com/en-us/library/bb624276\(v=office.15\)) property of the [ContactItem](https://msdn.microsoft.com/en-us/library/bb644956\(v=office.15\)) interface.

## Example

> [!NOTE] 
> The following code example is an excerpt from [Programming Applications for Microsoft Office Outlook 2007](https://www.amazon.com/gp/product/0735622493?ie=UTF8&tag=msmsdn-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0735622493).

An Electronic Business Card provides a contact view that captures specific information from that contact. The ContactItem interface provides specific members that pertain to Electronic Business Cards. These members are BusinessCardLayoutXml, [BusinessCardType](https://msdn.microsoft.com/en-us/library/bb612276\(v=office.15\)), [AddBusinessCardLogoPicture(String)](https://msdn.microsoft.com/en-us/library/bb646681\(v=office.15\)), [ForwardAsBusinessCard()](https://msdn.microsoft.com/en-us/library/bb646342\(v=office.15\)), [ResetBusinessCard()](https://msdn.microsoft.com/en-us/library/bb644057\(v=office.15\)), [SaveBusinessCardImage(String)](https://msdn.microsoft.com/en-us/library/bb623060\(v=office.15\)), and [ShowBusinessCardEditor()](https://msdn.microsoft.com/en-us/library/bb646685\(v=office.15\)).

In the following code example, BusinessCardLayoutExample modifies the layout of an Electronic Business Card by first obtaining a specified ContactItem object. In this case, the ContactItem is a contact with the value of the [Subject](https://msdn.microsoft.com/en-us/library/bb624088\(v=office.15\)) property equal to “Melissa MacBeth”. Next, BusinessCardLayoutExample creates an XML document class [XmlDocument](http://msdn2.microsoft.com/en-us/library/6kza7w4k), and then gets the layout attribute of this class in a string by using the BusinessCardLayoutXML value for the ContactItem object. The card layout is then changed from left-aligned to right-aligned.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following line of code shows how to do the import and assignment in C\#.

```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

```csharp
private void BusinessCardLayoutExample()
{
    Outlook.ContactItem contact =
        Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderContacts).Items.Find(
        "[Subject] = Melissa MacBeth'")
        as Outlook.ContactItem;
    if (contact != null)
    {
        XmlDocument doc = new XmlDocument();
        doc.LoadXml(contact.BusinessCardLayoutXml);
        XmlElement root = doc.DocumentElement;
        string layoutValue = root.GetAttribute("layout");
        if (layoutValue == "left")
        {
            root.SetAttribute("layout", "right");
            contact.BusinessCardLayoutXml = doc.OuterXml;
            contact.Save();
        }
    }
}
```

## See also



[Electronic Business Cards](electronic-business-cards.md)

