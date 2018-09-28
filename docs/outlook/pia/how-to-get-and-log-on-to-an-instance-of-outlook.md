---
title: 'Get and Log On to an Instance of Outlook'
TOCTitle: 'Get and Log On to an Instance of Outlook'
ms:assetid: 7f5057dc-4232-4dc7-b597-16ff5f7bcd7d
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff462097(v=office.15)
ms:contentKeyID: 55119926
ms.date: 07/24/2014
mtps_version: v=office.15
dev_langs:
- vb
- csharp
---

# Get and Log On to an Instance of Outlook

This topic shows how to obtain an [Application](https://msdn.microsoft.com/en-us/library/bb646615\(v=office.15\)) object that represents an active instance of Microsoft Outlook, if there is one running on the local computer, or to create a new instance of Outlook, log on to the default profile, and return that instance of Outlook.

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


The following code examples contain the GetApplicationObject method of the Sample class, implemented as part of an Outlook add-in project. Each project adds a reference to the Outlook Primary Interop Assembly, which is based on the [Microsoft.Office.Interop.Outlook](https://msdn.microsoft.com/en-us/library/bb610835\(v=office.15\)) namespace.

The GetApplicationObject method uses classes in the .NET Framework class library to check and obtain any Outlook process running on the local computer. It first uses the [GetProcessesByName](http://msdn2.microsoft.com/en-us/library/wbt7d3cy) method of the [Process](http://msdn2.microsoft.com/en-us/library/ccf1tfx0) class in the [System.Diagnostics](http://msdn2.microsoft.com/en-us/library/15t15zda) namespace to obtain an array of process components on the local computer that share the process name "OUTLOOK". To check whether the array does contain at least one Outlook process, GetApplicationObject uses Microsoft Language Integrated Query (LINQ). The [Enumerable](http://msdn2.microsoft.com/en-us/library/bb345746) class in the [System.Linq](http://msdn2.microsoft.com/en-us/library/bb336768) namespace provides a set of methods, including the [Count](http://msdn2.microsoft.com/en-us/library/bb357758) method, that implement the [IEnumerable\<T\>](http://msdn2.microsoft.com/en-us/library/9eekhta0) generic interface. Because the [Array](http://msdn2.microsoft.com/en-us/library/czz5hkty) class implements the IEnumerable(T) interface, GetApplicationObject can apply the Count method to the array returned by GetProcessesByName to see whether there is an Outlook process running. If there is, GetApplicationObject uses the [GetActiveObject](http://msdn2.microsoft.com/en-us/library/xt620x09) method of the [Marshal](http://msdn2.microsoft.com/en-us/library/asx0thw2) class in the [System.Runtime.InteropServices](https://msdn.microsoft.com/en-us/library/9esea608\(v=office.15\)) namespace to obtain that instance of Outlook, and casts that object to an Outlook [Application](https://msdn.microsoft.com/en-us/library/bb646615\(v=office.15\)) object.

If Outlook is not running on the local computer, GetApplicationObject creates a new instance of Outlook, uses the [Logon(Object, Object, Object, Object)](https://msdn.microsoft.com/en-us/library/bb646718\(v=office.15\)) method of the [NameSpace](https://msdn.microsoft.com/en-us/library/bb645857\(v=office.15\)) object to log on to the default profile, and returns that new instance of Outlook.

The following is the Visual Basic code example, followed by the C\# code example.

If you use Visual Studio to test this code example, you must first add a reference to the Microsoft Outlook 15.0 Object Library component and specify the Outlook variable when you import the Microsoft.Office.Interop.Outlook namespace. The Imports or using statement must not occur directly before the functions in the code example but must be added before the public Class declaration. The following lines of code show how to do the import and assignment in Visual Basic and C\#.

``` vb
Imports Outlook = Microsoft.Office.Interop.Outlook
```

``` csharp
using Outlook = Microsoft.Office.Interop.Outlook;
```

``` vb
Imports System.Diagnostics
Imports System.Linq
Imports System.Reflection
Imports System.Runtime.InteropServices
Imports Outlook = Microsoft.Office.Interop.Outlook

Namespace OutlookAddIn2
    Class Sample

        Function GetApplicationObject() As Outlook.Application

            Dim application As Outlook.Application

            ' Check whether there is an Outlook process running.
            If Process.GetProcessesByName("OUTLOOK").Count() > 0 Then

                ' If so, use the GetActiveObject method to obtain the process and cast it to an Application object.
                application = DirectCast(Marshal.GetActiveObject("Outlook.Application"), Outlook.Application)
            Else

                ' If not, create a new instance of Outlook and log on to the default profile.
                application = New Outlook.Application()
                Dim ns As Outlook.NameSpace = application.GetNamespace("MAPI")
                ns.Logon("", "", Missing.Value, Missing.Value)
                ns = Nothing
            End If

            ' Return the Outlook Application object.
            Return application
        End Function

    End Class
End Namespace
```

``` csharp
using System;
using System.Diagnostics;
using System.Linq;
using System.Reflection;
using System.Runtime.InteropServices;
using Outlook = Microsoft.Office.Interop.Outlook;

namespace OutlookAddIn1
{
    class Sample
    {
        Outlook.Application GetApplicationObject()
        {

            Outlook.Application application = null;

            // Check whether there is an Outlook process running.
            if (Process.GetProcessesByName("OUTLOOK").Count() > 0)
            {

                // If so, use the GetActiveObject method to obtain the process and cast it to an Application object.
                application = Marshal.GetActiveObject("Outlook.Application") as Outlook.Application;
            }
            else
            {

                // If not, create a new instance of Outlook and log on to the default profile.
                application = new Outlook.Application();
                Outlook.NameSpace nameSpace = application.GetNamespace("MAPI");
                nameSpace.Logon("", "", Missing.Value, Missing.Value);
                nameSpace = null;
            }

            // Return the Outlook Application object.
            return application;
        }

    }
}
```

## See also



[Sessions](sessions.md)

