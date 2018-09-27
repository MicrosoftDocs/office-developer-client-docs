---
title: 'How to: Access Solution-Specific Data Stored as a Hidden Message in a Folder'
TOCTitle: 'How to: Access Solution-Specific Data Stored as a Hidden Message in a Folder'
ms:assetid: bacf0562-1026-4c3b-87b0-4eaad5033592
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb623414(v=office.15)
ms:contentKeyID: 55119861
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# How to: Access Solution-Specific Data Stored as a Hidden Message in a Folder

This example shows how to use the [StorageItem](https://msdn.microsoft.com/en-us/library/bb623436\(v=office.15\)) object to retrieve data that is stored as a hidden message of a specific message class in a folder.

## Example

The StorageItem object is typically used to hide solution-specific data that cannot be displayed programmatically. In an Exchange environment, the StorageItem object is used to roam solution settings and ensure that these settings are available online and offline. You can assign a custom message class to the StorageItem object, or identify the object by subject.

The following code sample retrieves the XML data that is stored as a hidden message in the Calendar folder with the message class equal to IPM.Configuration.WorkHours.

The [PropertyAccessor](https://msdn.microsoft.com/en-us/library/bb646034\(v=office.15\)) object returns the XML as an object that contains a byte stream rather than a string representation of the XML. The code sample uses System.Text.Encoding.Ascii.GetString to convert the byte stream to a string.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The Imports or using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

``` vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` vb
Private Function GetWorkHoursXML() As String
    Try
        Dim storage As Outlook.StorageItem = _
            Application.Session.GetDefaultFolder( _
            Outlook.OlDefaultFolders.olFolderCalendar).GetStorage( _
            "IPM.Configuration.WorkHours", _
            Outlook.OlStorageIdentifierType.olIdentifyByMessageClass)
        Dim pa As Outlook.PropertyAccessor = storage.PropertyAccessor
        ' PropertyAccessor will return a byte array for this property
        Dim rawXmlBytes As Byte() = CType(pa.GetProperty( _
            "http://schemas.microsoft.com/mapi/proptag/0x7C080102"), _
            Byte())
        ' Use Encoding to convert the array to a string
        Return System.Text.Encoding.ASCII.GetString(rawXmlBytes)
    Catch
        Return String.Empty
    End Try
End Function
```

``` csharp
private string GetWorkHoursXML()
{
    try
    {
        Outlook.StorageItem storage =
            Application.Session.GetDefaultFolder(
            Outlook.OlDefaultFolders.olFolderCalendar).GetStorage(
            "IPM.Configuration.WorkHours",
            Outlook.OlStorageIdentifierType.olIdentifyByMessageClass);
        Outlook.PropertyAccessor pa = storage.PropertyAccessor;
        // PropertyAccessor will return a byte array for this property
        byte[] rawXmlBytes = (byte[])pa.GetProperty(
            "http://schemas.microsoft.com/mapi/proptag/0x7C080102");
        // Use Encoding to convert the array to a string
        return System.Text.Encoding.ASCII.GetString(rawXmlBytes);
    }
    catch
    {
        return string.Empty;
    }
}
```

## See also

#### Other resources

[Folders](folders.md)

