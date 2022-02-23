---
title: InfoPath 2003 compatible object models
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
keywords:
- infopath 2003-compatible form templates, object model,InfoPath 2003-compatible object model,object models [InfoPath 2003], compatible with InfoPath 2007,object models [InfoPath 2007], InfoPath 2003 compatible
ms.localizationpriority: medium
ms.assetid: e4511af6-d7e7-44ad-a50d-1b7ee04f8215
description: "Microsoft InfoPath is written as a Component Object Model (COM) application and exposes its programmability interfaces for both external automation and form template script as COM interfaces."
---

# InfoPath 2003 compatible object models

Microsoft InfoPath is written as a Component Object Model (COM) application and exposes its programmability interfaces for both external automation and form template script as COM interfaces. To support the creation of InfoPath solutions that use the Visual C# and Visual Basic managed-code languages, the InfoPath setup program installs three interop assemblies. Interop assemblies are .NET assemblies that act as a bridge between managed and unmanaged code, mapping COM object members to equivalent .NET managed members.
  
The files for the three interop assemblies installed by InfoPath are named:
  
- Microsoft.Office.Interop.InfoPath.dll
- Microsoft.Office.Interop.InfoPath.SemiTrust.dll
- Microsoft.Office.Interop.InfoPath.Xml.dll

This topic discusses the object model exposed through the Microsoft.Office.Interop.InfoPath.SemiTrust interop assembly, which is used exclusively for writing and running managed-code business logic from within InfoPath form templates (.xsn).
  
For information about the Microsoft.Office.Interop.InfoPath and Microsoft.Office.Interop.InfoPath.Xml assemblies, see the documentation for the [Microsoft.Office.Interop.InfoPath](https://msdn.microsoft.com/library/microsoft.office.interop.infopath.aspx) and [Microsoft.Office.Interop.InfoPath.Xml](https://msdn.microsoft.com/library/microsoft.office.interop.infopath.xml) namespaces.
  
## Important installation information

By default, the **Typical** installation option of the InfoPath setup program installs copies of the Microsoft.Office.Interop.InfoPath.SemiTrust and Microsoft.Office.Interop.InfoPath.Xml assemblies in the C:\Program Files\Microsoft Office\Office14 folder. The Microsoft.Office.Interop.InfoPath and Microsoft.Office.Interop.InfoPath.Xml assemblies are also installed in the Global Assembly Cache (GAC), the contents of which can be viewed from the C:\Windows\Assembly folder.
  
If these assemblies are not installed, you should confirm that Microsoft InfoPath was installed correctly. As long as the .NET Framework 2.0 or later is installed before running setup, the **.NET Programmability Support** option in the InfoPath setup program is set to **Run from My Computer** for a **Typical** installation of InfoPath. If these interop assemblies are not available on your computer, you must confirm that the .NET Framework 2.0 or later is installed, and then run **Add or Remove Programs** from the **Control Panel** and set the **.NET Programmability Support** option to **Run from My Computer**.
  
For information on downloading the .NET Framework 2.0 Redistributable, see [.NET Framework 2.0 Redistributable.](https://www.microsoft.com/downloads/details.aspx?displaylang=en&amp;FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5)
  
## The Microsoft.Office.Interop.InfoPath.SemiTrust namespace

Prior to the release of Microsoft Office InfoPath 2003 Service Pack 1 and the Microsoft Office InfoPath 2003 Toolkit for Visual Studio® .NET, all programming logic for InfoPath form templates was created using Microsoft JScript or Microsoft VBScript written in the Microsoft Script Editor (MSE) development environment. Script written in MSE is interpreted at run time and accesses the COM object model exposed by the IPEDITOR.dll dynamic link library.
  
To support the creation of form templates that use managed-code languages such as Visual C# and Visual Basic for programming logic, functionality was added to InfoPath to enable hosting the common language runtime (CLR) and the Microsoft.Office.Interop.InfoPath.SemiTrust interop assembly was created to enable managed code to interoperate with the COM object model exposed by InfoPath in a secure manner. For information on the security model that applies to InfoPath managed-code form templates, see [About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md).
  
Although the process of writing managed code for a given task in an InfoPath form template is very similar to performing the same programming task by writing script, the InfoPath 2003-compatible object model exposed when viewing the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace from the **Object Browser** in Visual Studio 2012 looks much more complex. This is because the .NET Framework interoperability technology used to support the InfoPath 2003-compatible object model requires a COM server to expose all of its public interfaces, as well as some additional constructs required by the .NET Framework itself.
  
### How COM objects are exposed to the InfoPath 2003 compatible object model

When working natively with a COM server from high-level languages such as JScript, VBScript, or Visual Basic (but not the .NET version of Visual Basic and Visual C#), the object model that is exposed is simpler than the underlying COM classes and interfaces. For example, when working from these languages, the InfoPath **UI** object exposes a set of seven methods, such as the **Alert** method for displaying a message box to users.
  
However, the underlying COM constructs that support the **UI** object are actually composed of three entities: two interfaces named **UI** and **UI2**, and a COM coclass that implements the members of these two interfaces. There are two versions of the **UI** interface because the COM framework requires the definition of an interface to remain fixed to maintain backward compatibility for programs and components that call an implementation of that interface.
  
In this case, the **UI** interface, which was defined for the initial release of InfoPath, provides four methods, including the **Alert** method. The **UI2** interface can be considered a second version of the **UI** interface, and it was defined for the InfoPath Service Pack 1 release. The **UI2** interface inherits the four methods of the original **UI** interface and adds three new methods, such as the **Confirm** method. Although you can write a line of code either in script or managed code that calls the **Confirm** method using `XDocument.UI.Confirm`, the underlying code is actually calling the **Confirm** method of the **UI2** interface from the implementation of that method in the COM coclass.
  
The object model as it is exposed to scripting hides these details, but the interop assembly required to work with a COM server from managed code exposes the coclass and both interfaces publicly. For the single **UI** object used in the MSE scripting environment, the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace exposes the following three items:
  
- [UI](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UI.aspx) interface
- [UI2](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UI2.aspx) interface
- [UIObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UIObject.aspx) coclass interface

Although all three of these interfaces are exposed in the **Object Browser** and are contained in the Class Library documentation for the namespace, you only work with the **UIObject** coclass interface, which implements the **UI** object, and with the members of the **UI2** interface, which is the most current version of the interface that is implemented by the **UIObject** coclass interface. To access the **UIObject** coclass interface from its parent [XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocument.aspx) object, just as in script, you use the [UI](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.UI.aspx) accessor property. Except for a few notable exceptions, this is the pattern for all objects from the original release of InfoPath that were updated when InfoPath Service Pack 1 was released.
  
While the pattern is basically the same, the situation is slightly simpler for the entirely new objects that were added in InfoPath Service Pack 1, such as the **Certificate** object. In this case, there are only two items to be concerned with: the [CertificateObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.CertificateObject.aspx) coclass interface and the members of the [Certificate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Certificate.aspx) interface, which is the most recent and only interface implemented by the **CertificateObject** coclass interface. Just as when using InfoPath COM objects from script, the [Certificate](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Signature.Certificate.aspx) accessor property is used to access the object from its parent.
  
This same pattern applies to the interfaces for collections, except the coclass interface for a collection has "Collection" appended to its name instead of "Object". For example, the coclass interface for the COM **DataAdapters** collection is named [DataAdaptersCollection](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataAdaptersCollection.aspx) and the interface it implements is the [DataAdapters](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataAdapters.aspx) interface. Similarly, the [DataAdapters](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.DataAdapters.aspx) accessor property of the **XDocument** parent object is used to access the collection.
  
There are three exceptions to this naming pattern. The coclass interfaces for the COM **Application** and **XDocument** objects do not have "Object" appended to their names. Their names are identical to their corresponding COM objects: [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Application.aspx) and **XDocument**. Additionally, the names of the interfaces implemented by the **Application** and **XDocument** coclass interfaces are prefixed with the underscore character (_): [_Application2](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._Application2.aspx) and [_XDocument2](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.aspx). The third exception is the COM **DataObject** object. The coclass interface for this object is named [DataSourceObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataSourceObject.aspx) , but just like other InfoPath COM objects, the interface it implements is the [DataObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.DataObject.aspx) interface.
  
### How Microsoft XML Core Services (MSXML) 5.0 for Microsoft Office objects are exposed to the InfoPath 2003 compatible object model

A subset of the objects and members of the object model provided by Microsoft XML Core Services (MSXML), which is also a COM server, are wrapped by interfaces exposed by the Microsoft.Office.Interop.InfoPath.SemiTrust interop assembly. The reason this is necessary is that some of the members of the InfoPath COM object model rely on MSXML and must be able to access these members in a secure manner. The names of interfaces in the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace that wrap the objects and members of the MSXML object model are the same as the names exposed by the MSXML COM server. In most cases, these names are prefixed with "IXMLDOM" because they are used to work with the XML Document Object Model (DOM). For example, the [DOM](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._XDocument2.DOM.aspx) property of the **XDocument** interface, which is used to return a reference to a form's underlying XML document, returns the [IXMLDOMDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.IXMLDOMDocument.aspx) interface that is wrapped by the Microsoft.Office.Interop.InfoPath.SemiTrust interop assembly. You call and use the members of the **IXMLDOMDocument** interface in basically the same way as when using script in form templates that don't use managed code.
  
For more information on using members of the Microsoft XML Core Services (MSXML) for Microsoft Office object model in managed-code form templates, see [Working with MSXML and System.Xml Using the InfoPath 2003 Object Model](working-with-msxml-and-system-xml-using-the-infopath-2003-object-model.md).
  
### Using IntelliSense

For most of the code you write against the InfoPath 2003-compatible object model in a managed-code form template, you will use the `thisXDocument` and `thisApplication` variables that are initialized in the `_Startup` method of the default FormCode.cs or FormCode.vb class file. You can use the `thisXDocument` and `thisApplication` variables to access the members of the [XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocument.aspx) and [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Application.aspx) coclass interfaces. After you type the name of either variable followed by a period, IntelliSense statement completion will display the list members of the corresponding coclass interface. You can continue in this fashion to access the object model member you want to work with.
  
The following shows a simple example that uses the `thisXDocument` variable to access the [Alert](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UI2.Alert.aspx) method to display the version of the InfoPath application by using the [Version](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust._Application2.Version.aspx) property accessed from the  `thisApplication` variable.
  
```cs
thisXDocument.UI.Alert(thisApplication.Version);
```

```vb
thisXDocument.UI.Alert(thisApplication.Version)
```

### Using the Class Library reference documentation

The organization of the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace Class Library reference documentation reflects the relationships between coclass interfaces and the inherited interfaces they implement. This is described in the "How COM Objects are Exposed to Managed Code" section earlier in this topic.
  
Although the organization and naming of the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace reference documentation appears confusing at first, the topics are basically organized in the same way as the InfoPath Object Model Reference that is part of the InfoPath Developer's Reference, which is included with InfoPath. With the exception of the topics for the **Application** and **XDocument** interfaces, all of the COM coclass interface topics map to the equivalent "Object" and "Collection" topics from the InfoPath scripting reference. For example, the "UIObject Interface" and the "WindowsCollection Interface" topics of the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace reference documentation correspond to similar content in the "UI Object" and "Windows Collection" topics of the InfoPath Object Model Reference scripting reference.
  
However, the link to the members of the coclass interface following the description of the interface at the beginning of the topic displays an empty topic. To display the list of members that are implemented by the coclass interface, you must open the topic for the most recent interface that is inherited by the coclass, and then open the table of its members. A link to the inherited interface is provided at the beginning of the Remarks section in the coclass interface topic.
  
When you press F1 in the Code Editor, the behavior is similar, except that the member on which you invoke F1 Help will be displayed directly, because you are most typically working with members of an interface. However, the fact that a member can be implemented from a versioned interface may be confusing the first time you encounter it. For example, if you type `thisXDocument.UI.Alert` and place the cursor on `Alert` and press F1, a topic titled "UI2.Alert Method" is displayed. This is because the **Alert** method is an implementation of a member of the **UI2** interface.
  
### Passing optional parameters to InfoPath object model members

If an InfoPath 2003-compatible object model member contains an optional parameter, and you do not specify a value for that parameter, you must pass the **Type.Missing** field for that parameter instead. Failure to pass the **Type.Missing** field when an actual value is omitted will result in a build error. This is true for code written in both Visual C# and Visual Basic. For example, the [SelectNodes](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.View.SelectNodes.aspx) method of the [ViewObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.ViewObject.aspx) interface includes two optional parameters:  _varEndNode_ and  _varViewContext_. A line of code that does not specify actual values for these optional parameters should look like the following examples.
  
```cs
IXMLDOMNode group1 = 
   thisXDocument.DOM.selectSingleNode("/my:myFields/my:group1");
thisXDocument.View.SelectNodes(group1, Type.Missing, Type.Missing);
```

```vb
Dim group1 As IXMLDOMNode = _
   thisXDocument.DOM.selectSingleNode("/my:myFields/my:group1")
thisXDocument.View.SelectNodes(group1, Type.Missing, Type.Missing)
```

### About common language specification compliance

Internally, every interface and member in the Microsoft.Office.Interop.InfoPath.SemiTrust assembly has its **CLSCompliant** attribute set to **false**. Because the reference documentation is generated in part using **System.Reflection**, the description of each interface and member has the phrase "This interface/method/property is not CLS-compliant" appended to it. However, most of the interfaces and members of the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace actually are CLS-compliant.
  
## See also

- [Common Tasks for Developing Form Templates Using the InfoPath 2003 Object Model](common-tasks-for-developing-form-templates-using-infopath-object-model.md)
- [About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md)
- [Creating Form Templates Using the InfoPath 2003 Object Model](creating-form-templates-using-the-infopath-2003-object-model.md)
- [Understanding the InfoPath 2003 Object Model](understanding-the-infopath-2003-object-model.md)
