---
title: Import appointment XML data into Outlook appointment objects
TOCTitle: Import appointment XML data into Outlook appointment objects
ms:assetid: 166a648a-1c48-4984-8889-a7614cc277b1
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff462092(v=office.15)
ms:contentKeyID: 55119821
ms.date: 07/24/2014
mtps_version: v=office.15
---

# Import appointment XML data into Outlook appointment objects

This topic shows how to read appointment data formatted in XML, save the data to Outlook [AppointmentItem](https://msdn.microsoft.com/en-us/library/bb645611\(v=office.15\)) objects in the default calendar, and return the appointment objects in an array.

## Example

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p>Helmut Obertanner provided the following code examples. Helmut's expertise is in Office Developer Tools for Visual Studio and Outlook. Helmut maintains a professional site at <a href="http://www.outlooksharp.de/">X4Uelectronix</a>.</p></td>
</tr>
</tbody>
</table>


The following code examples contain the CreateAppointmentsFromXml method of the Sample class, implemented as part of an Outlook add-in project. Each project adds a reference to the Outlook Primary Interop Assembly, which is based on the [Microsoft.Office.Interop.Outlook](https://msdn.microsoft.com/en-us/library/bb610835\(v=office.15\)) namespace.

The CreateAppointmentsFromXml method accepts two input parameters:

  - application is a trusted Outlook [Application](https://msdn.microsoft.com/en-us/library/bb646615\(v=office.15\)) object.

  - xml is either an XML string, or a string that represents a path to a valid XML file. For the purpose of the following code examples, the XML delimits appointment data by using the following XML tags:
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>Appointment data</p></th>
    <th><p>Delimiting XML tag</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Entire set of appointment data</p></td>
    <td><p>appointments</p></td>
    </tr>
    <tr class="even">
    <td><p>Each appointment in the set</p></td>
    <td><p>appointment</p></td>
    </tr>
    <tr class="odd">
    <td><p>Start time of an appointment</p></td>
    <td><p>starttime</p></td>
    </tr>
    <tr class="even">
    <td><p>End time of an appointment</p></td>
    <td><p>endtime</p></td>
    </tr>
    <tr class="odd">
    <td><p>Title of an appointment</p></td>
    <td><p>subject</p></td>
    </tr>
    <tr class="even">
    <td><p>Location of an appointment</p></td>
    <td><p>location</p></td>
    </tr>
    <tr class="odd">
    <td><p>Details of an appointment</p></td>
    <td><p>body</p></td>
    </tr>
    </tbody>
    </table>


The following example shows input data for the xml parameter.

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<appointments>
    <appointment>
        <starttime>2009-06-01T15:00:00</starttime>
        <endtime>2009-06-01T16:15:00</endtime>
        <subject>This is a Test-Appointment</subject>
        <location>At your Desk</location>
        <body>Here is the Bodytext</body>
    </appointment>
    <appointment>
        <starttime>2009-06-01T17:00:00</starttime>
        <endtime>2009-06-01T17:15:00</endtime>
        <subject>This is a second Test-Appointment</subject>
        <location>At your Desk</location>
        <body>Here is the Bodytext</body>
    </appointment>
    <appointment>
        <starttime>2009-06-01T17:00:00</starttime>
        <endtime>2009-06-01T18:15:00</endtime>
        <subject>This is a third Test-Appointment</subject>
        <location>At your Desk</location>
        <body>Here is the Bodytext</body>
    </appointment>
</appointments>
```

The CreateAppointmentsFromXml method uses the Microsoft COM implementation of the XML Document Object Model (DOM) to load and process the XML data that xml provides. CreateAppointmentsFromXml first checks whether xml specifies a valid source of XML data. If so, it loads the data into an XML document, [DOMDocument](https://msdn.microsoft.com/en-us/library/ms756987\(v=office.15\)). Otherwise, CreateAppointmentsFromXml throws an exception. For more information about the XML DOM, see [DOM](https://msdn.microsoft.com/en-us/library/ms766487\(v=office.15\)).

For each appointment child node delimited by the appointment tag in the XML data, CreateAppointmentsFromXml looks for specific tags, uses the DOM to extract the data, and assigns the data to corresponding properties of an **AppointmentItem** object: [Start](https://msdn.microsoft.com/en-us/library/bb647263\(v=office.15\)), [End](https://msdn.microsoft.com/en-us/library/bb623715\(v=office.15\)), [Subject](https://msdn.microsoft.com/en-us/library/bb611653\(v=office.15\)), [Location](https://msdn.microsoft.com/en-us/library/bb608946\(v=office.15\)), and [Body](https://msdn.microsoft.com/en-us/library/bb644880\(v=office.15\)). CreateAppointmentsFromXml then saves the appointment to the default calendar.

CreateAppointmentsFromXml uses the [Add](http://msdn2.microsoft.com/en-us/library/3wcytfd1) method of the [List\<T\>](http://msdn2.microsoft.com/en-us/library/6sh2ey19) class in the [System.Collections.Generic](http://msdn2.microsoft.com/en-us/library/0sbxh9x2) namespace to aggregate these AppointmentItem objects. When the method has processed all the appointments in the XML data, it returns the AppointmentItem objects in an array.

If you use Visual Studio to test this code example, you must first add a reference to the **Microsoft Outlook 15.0 Object Library** component and specify the Outlook variable when you import the **Microsoft.Office.Interop.Outlook** namespace. The **Imports** or **using** statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.


```vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```



```csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

The following is the Visual Basic code example, followed by the C\# code example.



```vb
Imports System.IO
Imports System.Xml
Imports Outlook = Microsoft.Office.Interop.Outlook

Namespace OutlookAddIn2
    Class Sample
        Function CreateAppointmentsFromXml(ByVal application As Outlook.Application, _
            ByVal xml As String) As Outlook.AppointmentItem()

            Dim appointments As New List(Of Outlook.AppointmentItem)
            Dim xmlDoc As New XmlDocument()

            ' If xml is an XML string, create the XML document directly.
            If xml.StartsWith("<?xml") Then
                xmlDoc.LoadXml(xml)
            ElseIf (File.Exists(xml)) Then
                xmlDoc.Load(xml)
            Else
                Throw New Exception("The input string is not valid XML data or the specified file doesn't exist.")
            End If


            ' Select all appointment nodes under the root appointments node.
            Dim appointmentNodes As XmlNodeList = xmlDoc.SelectNodes("appointments/appointment")

            For Each appointmentNode As XmlNode In appointmentNodes

                ' Create a new AppointmentItem object.
                Dim newAppointment As Outlook.AppointmentItem = _
                    DirectCast(application.CreateItem(Outlook.OlItemType.olAppointmentItem), _
                    Outlook.AppointmentItem)

                ' Loop over all child nodes, check the node name, and import the data into the appointment fields.

                For Each node As XmlNode In appointmentNode.ChildNodes
                    Select Case (node.Name)

                        Case "starttime"
                            newAppointment.Start = DateTime.Parse(node.InnerText)


                        Case "endtime"
                            newAppointment.End = DateTime.Parse(node.InnerText)


                        Case "subject"
                            newAppointment.Subject = node.InnerText


                        Case "location"
                            newAppointment.Location = node.InnerText


                        Case "body"
                            newAppointment.Body = node.InnerText


                    End Select
                Next

                ' Save the item in the default calendar.
                newAppointment.Save()
                appointments.Add(newAppointment)
            Next

            ' Return an array of new appointments.
            Return appointments.ToArray()
        End Function


    End Class
End Namespace
```



```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using System.Xml;
using Outlook = Microsoft.Office.Interop.Outlook;

namespace OutlookAddIn1
{
    class Sample
    {
        Outlook.AppointmentItem[] CreateAppointmentsFromXml(Outlook.Application application, 
            string xml)
        {
            // Create a list of appointment objects.
            List<Outlook.AppointmentItem> appointments = new 
                List<Microsoft.Office.Interop.Outlook.AppointmentItem>();
            XmlDocument xmlDoc = new XmlDocument();

            // If xml is an XML string, create the document directly. 
            if (xml.StartsWith("<?xml"))
            {
                xmlDoc.LoadXml(xml);
            }
            else if (File.Exists(xml))
            {
                xmlDoc.Load(xml);
            }
            else
            {
                throw new Exception(
                    "The input string is not valid XML data or the specified file doesn't exist.");
            }

            // Select all appointment nodes under the root appointments node.
            XmlNodeList appointmentNodes = xmlDoc.SelectNodes("appointments/appointment");
            foreach (XmlNode appointmentNode in appointmentNodes)
            {

                // Create a new AppointmentItem object.
                Outlook.AppointmentItem newAppointment = 
                    (Outlook.AppointmentItem)application.CreateItem(Outlook.OlItemType.olAppointmentItem);

                // Loop over all child nodes, check the node name, and import the data into the 
                // appointment fields.
                foreach (XmlNode node in appointmentNode.ChildNodes)
                {
                    switch (node.Name)
                    {

                        case "starttime":
                            newAppointment.Start = DateTime.Parse(node.InnerText);
                            break;

                        case "endtime":
                            newAppointment.End = DateTime.Parse(node.InnerText);
                            break;

                        case "subject":
                            newAppointment.Subject = node.InnerText;
                            break;

                        case "location":
                            newAppointment.Location = node.InnerText;
                            break;

                        case "body":
                            newAppointment.Body = node.InnerText;
                            break;

                    }
                }

                // Save the item in the default calendar.
                newAppointment.Save();
                appointments.Add(newAppointment);
            }

            // Return an array of new appointments.
            return appointments.ToArray();
        }

    }
}
```

## See also

- [Appointments](appointments.md)

