---
title: 'How to: Save a Calendar to Disk'
TOCTitle: 'How to: Save a Calendar to Disk'
ms:assetid: f1b57bd0-c972-4b86-8870-f26290f28050
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Bb647583(v=office.15)
ms:contentKeyID: 55119827
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# How to: Save a Calendar to Disk

This example shows how to save an entire calendar to disk in the iCalendar (.ics) file format.

## Example

This code sample uses the [CalendarSharing](https://msdn.microsoft.com/en-us/library/bb624344\(v=office.15\)) object that supports saving a whole calendar or a range of appointments from the calendar to disk. Outlook automatically optimizes an .ics file so that recurring appointments are not saved as individual appointments in the .ics file. Depending on the size of the calendar being saved, saving a calendar to disk can take a significant amount of time. While saving the calendar, the Outlook window appears unresponsive to the user.

The code sample first calls [GetCalendarExporter](https://msdn.microsoft.com/en-us/library/bb610021\(v=office.15\)) on the default Calendar folder to obtain a CalendarSharing object. Then it sets properties of the CalendarSharing object to specify criteria for the export, such as whether to save the entire calendar and include details of appointments that are marked "private".

To save the calendar information in .ics file format, the code sample calls the [SaveAsICal](https://msdn.microsoft.com/en-us/library/bb644844\(v=office.15\)) method of the CalendarSharing object.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The Imports or using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

``` vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` vb
Private Sub SaveCalendarToDisk(ByVal calendarFileName As String)
    If String.IsNullOrEmpty(calendarFileName) Then
        Throw New ArgumentException( _
        "Parameter must contain a value.", "calendarFileName")
    End If

    Dim calendar As Outlook.Folder = TryCast( _
        Application.Session.GetDefaultFolder(_
        Outlook.OlDefaultFolders.olFolderCalendar), Outlook.Folder)
    Dim exporter As Outlook.CalendarSharing = _
        calendar.GetCalendarExporter()

    '' Set the properties for the export
    exporter.CalendarDetail = Outlook.OlCalendarDetail.olFullDetails
    exporter.IncludeAttachments = True
    exporter.IncludePrivateDetails = True
    exporter.RestrictToWorkingHours = False
    exporter.IncludeWholeCalendar = True

    '' Save the calendar to disk
    exporter.SaveAsICal(calendarFileName)
End Sub
```

``` csharp
private void SaveCalendarToDisk(string calendarFileName)
{
    if (string.IsNullOrEmpty(calendarFileName))
        throw new ArgumentException("calendarFileName", 
        "Parameter must contain a value.");

    Outlook.Folder calendar = Application.Session.GetDefaultFolder(
        Outlook.OlDefaultFolders.olFolderCalendar) as Outlook.Folder;
    Outlook.CalendarSharing exporter = calendar.GetCalendarExporter();

    // Set the properties for the export
    exporter.CalendarDetail = Outlook.OlCalendarDetail.olFullDetails;
    exporter.IncludeAttachments = true;
    exporter.IncludePrivateDetails = true;
    exporter.RestrictToWorkingHours = false;
    exporter.IncludeWholeCalendar = true;

    // Save the calendar to disk
    exporter.SaveAsICal(calendarFileName);
}
```

## See also

#### Other resources

[Calendar](calendar.md)

