---
title: About the Microsoft Office InfoPath Primary Interop Assembly
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
keywords:
- infopath 2007, primary interop assembly,InfoPath primary interop assembly,PIAs [InfoPath 2007],primary interop assemblies [InfoPath 2007]
ms.localizationpriority: medium
ms.assetid: 1b3ae03c-6951-49e4-a489-4712d3f7ba72
description: "To support the creation of InfoPath solutions that use managed-code languages such as Visual C# and Visual Basic, the .NET Programmability Support option in the InfoPath setup program installs three interop assemblies."
---

# About the Microsoft Office InfoPath Primary Interop Assembly

The InfoPath application is built as a Component Object Model (COM) application that exposes its programmability interfaces for external automation as COM interfaces. To support the creation of InfoPath solutions that use managed-code languages such as Visual C# and Visual Basic, the **.NET Programmability Support** option in the InfoPath setup program installs three interop assemblies. Interop assemblies are .NET assemblies that act as a bridge between managed and unmanaged code, mapping COM object members to equivalent .NET managed members.
  
The files for the three interop assemblies installed by InfoPath are named:
  
- Microsoft.Office.Interop.InfoPath.dll

- Microsoft.Office.Interop.InfoPath.SemiTrust.dll

- Microsoft.Office.Interop.InfoPath.Xml.dll

This topic discusses the object model exposed through the Microsoft.Office.Interop.InfoPath interop assembly, which is used exclusively for external automation code. For information on the Microsoft.Office.Interop.InfoPath.SemiTrust assembly, which is used exclusively for writing and running managed code that runs from within InfoPath form templates (.xsn), see [InfoPath 2003 Compatible Object Models](https://msdn.microsoft.com/library/e4511af6-d7e7-44ad-a50d-1b7ee04f8215%28Office.15%29.aspx).
  
## Important Installation Information

The default installation option of the InfoPath setup program installs the Microsoft.Office.Interop.InfoPath assembly in the Global Assembly Cache (GAC), the contents of which can be viewed from the C:\Windows\Assembly folder (or in C:\Windows\assembly\GAC_MSIL when viewing the file system directly). This assembly is referred to as the "Microsoft Office InfoPath Primary Interop Assembly" and is often used in conjunction with the Microsoft.Office.Interop.InfoPath.Xml assembly, which is also installed in the GAC, to automate the InfoPath application from external applications that use managed code. For information about the Microsoft.Office.Interop.InfoPath.Xml assembly, see [About the InfoPath XML Interop Assembly](about-the-infopath-xml-interop-assembly.md).
  
If the Microsoft.Office.Interop.InfoPath assembly is not visible in the GAC, you should confirm that InfoPath was installed correctly. By default, the **.NET Programmability Support** option in the setup program is set to **Run from My Computer** as long as the .NET Framework 1.1 Redistributable, .NET Framework 1.1 Software Development Kit (SDK), or a later version of the .NET Framework is installed before running setup. If these interop assemblies are not available on your computer, you must confirm that .NET Framework 1.1 or later is installed, and then use **Programs and Features** from the **Control Panel** to change setup by setting the **.NET Programmability Support** option under **Microsoft Office InfoPath** to **Run from My Computer**.
  
For information about downloading the .NET Framework 1.1 Redistributable, see [.NET Framework 1.1 Redistributable](/download/dotnet-framework).
  
## The Microsoft.Office.Interop.InfoPath Namespace

Although the process of writing managed code for a given task is very similar to performing the same task using a language such as Visual Basic for Applications or JScript, the object model exposed when viewing the **Microsoft.Office.Interop.InfoPath** namespace from the **Object Browser** in Microsoft Visual Studio looks more complex. This is because interoperability with the .NET Framework requires a COM server to expose all of its public interfaces, as well as some additional constructs required by the .NET Framework itself. For more information on how and why the object model exposed by an interop assembly appears more complex, see the "How COM Objects are Exposed to Managed Code" section of the [InfoPath 2003 Compatible Object Models](../form-templates/infopath-2003-compatible-object-models.md) topic.
  
### Using IntelliSense

The examples in this section assume that you have established references to the Microsoft.Office.Interop.InfoPath and Microsoft.Office.Interop.InfoPath.Xml assemblies. For information on how to set references and additional external automation examples, see [External Automation Scenarios and Examples](external-automation-scenarios-and-examples.md).
  
Before you can use Microsoft IntelliSense statement completion in external automation code, you must create an object variable for an instance of the [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.Application.aspx) class as shown in the following line of code.
  
```cs
Application myApp = 
    new Microsoft.Office.Interop.InfoPath.Application();
```

```vb
Dim myApp As Application = _
    New Microsoft.Office.Interop.InfoPath.Application()
```

After creating the object variable, when you type the variable name followed by a period, a drop-down list is displayed with members of the **Application** class to select.
  
To work with an InfoPath form, declare an object variable of type [XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.XDocument.aspx) , and then initialize it by opening the form from the [XDocuments](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.XDocuments.aspx) collection of the **Application** object variable as shown in the following line of code.
  
```cs
XDocument myXDoc = myApp.XDocuments.Open(
    "c:\\temp\\Form1.xml",
    (int) XdDocumentVersionMode.xdFailOnVersionOlder);
```

```vb
Dim myXDoc As XDocument = myApp.XDocuments.Open( _
    "c:\\temp\\Form1.xml", _
    XdDocumentVersionMode.xdFailOnVersionOlder)
```

The IntelliSense statement completion drop-down list for members of the **XDocument** class will be displayed when you type the name of the variable followed by a period.
  
To work with the contents of the underlying XML document for the form using Microsoft XML Core Services (MSXML), you must create a variable of type [IXMLDOMDocument2](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.Xml.IXMLDOMDocument2.aspx) , and then use the [DOM](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath._XDocument2.DOM.aspx) property of the **XDocument** class to assign the XML Document Object Model (DOM) of the form to that variable.
  
```cs
IXMLDOMDocument2 doc= myXDoc.DOM as IXMLDOMDocument2;
```

```vb
Dim doc As IXMLDOMDocument2 = myXDoc.DOM
```

The IntelliSense statement completion drop-down list for members of the **IXMLDOMDocument2** class will be displayed when you type the name of the variable followed by a period, which allows you to use MSXML to work with the XML document.
  
### Using the Class Library Reference Documentation

The organization of the [Microsoft.Office.Interop.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.aspx) namespace Class Library reference documentation reflects the relationships between coclass interfaces and the inherited interfaces they implement.
  
When you open a topic for a coclass interface, such as [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.Application.aspx) , the link to the members of the coclass interface following the description of the interface at the beginning of the topic displays an empty topic. To display the list of members that are implemented by the coclass interface, you must open the topic for the most recent interface that is inherited by the coclass, and then open the table of its members. A link to the inherited interface is provided at the beginning of the Remarks section in the coclass interface topic.
  
When you press F1 in the Visual Studio Code Editor, the behavior is similar, except that the member on which you invoke F1 Help will be displayed directly, because you are most typically working with members of an interface. However, the fact that a member can be implemented from a versioned interface may be confusing the first time you encounter it. For example, if you type `myXDocument.UI.Alert` and place the cursor on `Alert` and press F1, a topic titled "UI2.Alert Method" is displayed. This is because the **Alert** method is an implementation of a member of the **UI2** interface.
  
### Passing Optional Parameters to InfoPath Object Model Members

If an InfoPath object model member contains an optional parameter, and you do not specify a value for that parameter, you must pass the **Type.Missing** field for that parameter. Failure to pass the **Type.Missing** field when an actual value is omitted will result in a build error. This is true for code written in both C# and Visual Basic. For example, the [SelectNodes](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.View2.SelectNodes.aspx) method of the [ViewObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.ViewObject.aspx) interface includes two optional parameters: _varEndNode_ and _varViewContext_. A line of code that does not specify actual values for these optional parameters should look like the following examples.
  
```cs
myXDocument.View.SelectNodes(group1, Type.Missing, Type.Missing);
```

```vb
myXDocument.View.SelectNodes(group1, Type.Missing, Type.Missing)
```

## See also

- [External automation scenarios and examples](external-automation-scenarios-and-examples.md)
