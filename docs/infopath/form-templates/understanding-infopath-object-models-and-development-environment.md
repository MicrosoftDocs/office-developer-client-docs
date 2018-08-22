---
title: "Understanding InfoPath Object Models and Development Environment"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
keywords:
- infopath 2007, object models,object models [InfoPath 2007],InfoPath 2007, development environments
localization_priority: Normal
ms.assetid: 29415c5b-9a42-46f4-a9e8-6a7d5bb7bdbf
description: "Microsoft InfoPath 2013 supports two kinds of programming models for developing business logic in form templates, and supports external automation from managed code."
---

# Understanding InfoPath Object Models and Development Environment

Microsoft InfoPath 2013 supports two kinds of programming models for developing business logic in form templates, and supports external automation from managed code.
  
InfoPath Forms Services, which is available in SharePoint Server 2013, provides a Web browser experience for filling out InfoPath forms. When deployed to a server that runs InfoPath Forms Services, forms that are based on browser-compatible form templates (.xsn) can be opened in a Web browser from computers that do not have InfoPath installed, but they will open in InfoPath when it is installed. InfoPath Forms Services also provides an object model for automating server tasks related to InfoPath form template publishing and administration.
  
InfoPath 2013 supports the Visual Studio 2012 programming environment and its associated programming languages, which are described later in this topic.
  
## InfoPath Programming Models

InfoPath 2013 supports two object models for developing business logic in form templates:
  
- The InfoPath Managed Code Object Model
    
- The InfoPath 2003-Compatible Managed Code Object Model
    
Additionally, InfoPath 2013 enables writing managed code to automate InfoPath from an external application.
  
InfoPath Forms Services provides an object model for automating server tasks, such as verifying and uploading form templates from code running on the server, which requires server administrator access and permissions.
  
> [!NOTE]
> The InfoPath Filler 2013 can open and run InfoPath form template solutions created in earlier versions of InfoPath that use business logic written with scripting languages (JScript and VBScript). However, InfoPath Designer 2010 does not support creating or modifying form templates that use business logic written with script. 
  
### The InfoPath Managed Code Object Model

The InfoPath 2013 managed code object model is implemented in two assemblies both of which are named Microsoft.Office.Infopath.dll.
  
One version of the assembly implements a subset of the InfoPath object model that contains only the types and members that are supported in the business logic of form templates deployed as browser-enabled form templates running on SharePoint Server 2013 with InfoPath Forms Services. Form templates with business logic written against this assembly will open and run in the InfoPath Filler and in a Web browser.
  
The other version of the assembly implements additional types and members that provide functionality that is not supported in the business logic of browser-enabled form templates. Form templates with business logic written against the additional classes and members in this assembly will open and run only in the InfoPath Filler editor.
  
> [!NOTE]
> It is possible to write conditional logic that uses the properties of the [Environment](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Environment.aspx) class to determine which environment (InfoPath Filler or a Web browser) the form template is running in. By using this conditional logic, your business logic can branch between code that works in a Web browser and code written against classes and members that work only in the InfoPath Filler editor. For more information, see [Write Conditional Logic That Determines the Run-time Environment](how-to-write-conditional-logic-that-determines-the-run-time-environment.md)
  
The assembly that InfoPath uses when you add and compile business logic for the form template depends on whether you select the **Blank Form** or **Blank Form (InfoPath Filler)** form template on the **New** tab of the Microsoft Office Backstage when you start to design a new form in the InfoPath Designer. Forms created by using the **Blank Form** form template use the assembly that contains only the types and members that are supported in the business logic of form templates deployed as browser-enabled form templates. Forms created by using the **Blank Form** form template can be opened in both the Web browser and the InfoPath Filler. Forms created by using the **Blank Form (InfoPath Filler)** form template use the assembly that implements additional types and members that provide functionality that is not supported in the business logic of browser-enabled form templates, and can only be opened in the InfoPath Filler. 
  
> [!TIP]
> After you start to design a form template, you can change which assembly is used by changing the form compatibility settings. To do that, click **Language** on the **Developer** tab, and then click **Compatibility** in the **Category** list. In the **Form type** list, select **Web Browser Form** to create a form that can be deployed as a browser-compatible form on SharePoint Server 2013. Select **InfoPath Filler Form** to create a form that can run only in the InfoPath Filler editor. The other selections in the **Form type** list provide support for compatibility with InfoPath 2007 and InfoPath 2003. 
  
The classes and members of both versions of this object model are exposed through the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace. The following table lists where the assemblies are located in the directories of an InfoPath 2013 installation. 
  
|**Assembly**|**Description**|
|:-----|:-----|
|Microsoft.Office.InfoPath.dll           (located in C:\Program Files\Microsoft Office\Office15\InfoPathOM\InfoPathOMFormServices)  <br/> |The subset of the object model that contains only types and members that will run in the business logic of a form template deployed to a server that runs InfoPath Forms Services.  <br/> |
|Microsoft.Office.InfoPath.dll           (located in C:\Program Files\Microsoft Office\Office15\InfoPathOM)  <br/> |The "full" object model including types and members that will not run in the business logic of a form template deployed to InfoPath Forms Services.  <br/> |
   
> [!NOTE]
> The assemblies referenced earlier in this section are used at design time when you write and compile code. At run time, the assembly used when a form template is opened in InfoPath is located in the Global Assembly Cache (GAC) of the computer on which InfoPath is installed. When a form template is opened in a Web browser from a server that runs InfoPath Forms Services, the assembly used is located on the server. 
  
Providing two assemblies helps ensure that your business logic will contain only calls to the appropriate object model members for the supported form editors (Web browser or InfoPath Filler). For example, when you edit your code, IntelliSense features such as statement completion and in-line documentation will only display and work against the appropriate object model members for your target form editors.
  
In both versions of the managed code object model exposed by the Microsoft.Office.InfoPath assembly, navigating and updating XML data stores in business logic requires calls to the members of the **System.Xml.XPath.XPathNavigator** class. In InfoPath 2003, navigating and updating XML data stores requires calling members of MSXML classes (for business logic created by using JScript or VBScript) or by calling through the wrappers for MSXML classes that are provided by the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace (for business logic created by using C# or Visual Basic and the Microsoft Office InfoPath 2003 Toolkit for Visual Studio .NET). 
  
Using members of the **XPathNavigator** class allows the same business logic code to support DOM manipulation for form templates that are opened in both the InfoPath client and in Web-enabled forms opened from SharePoint Server 2013 with InfoPath Forms Services in a Web browser. 
  
For information about how to work with members of the **XPathNavigator** class in the business logic of InfoPath managed code form templates, see [Work with the XPathNavigator and XPathNodeIterator Classes](how-to-work-with-the-xpathnavigator-and-xpathnodeiterator-classes.md).
  
### The InfoPath 2003-Compatible Managed Code Object Model

The InfoPath 2003-compatible managed code object model was introduced in InfoPath 2003 Service Pack 1 together with the Microsoft Office InfoPath 2003 Toolkit for Visual Studio .NET for writing business logic in form templates with managed code. This object model is still supported by InfoPath 2013 to provide compatibility with InfoPath 2003.
  
The classes and members of this object model are exposed through the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace. This object model is implemented in the following assembly file which is located in the C:\Program Files\Microsoft Office\Office14 folder. 
  
|**Assembly**|**Description**|
|:-----|:-----|
|Microsoft.Office.Interop.InfoPath.SemiTrust.dll  <br/> |Provides COM interop against the InfoPath COM object model for form template business logic written using C# or Visual Basic.  <br/> |
   
> [!NOTE]
> Although creating business logic with the COM interop managed-code object model provided by the Microsoft.Office.Interop.InfoPath.SemiTrust assembly is still supported by InfoPath 2013, business logic written using this object model it is not supported for browser-enabled form templates deployed to SharePoint Server 2013 with InfoPath Forms Services. Browser-enabled form templates must use the InfoPath managed code object model for custom business logic. 
  
### Automating InfoPath from Managed Code

In addition to writing business logic with managed code, developers can automate InfoPath by using managed code running in an external application. This functionality and the assemblies required for writing code were introduced in InfoPath 2003 Service Pack 1. The objects and members for automating InfoPath have been updated to provide additional functionality when you write external automation code for InfoPath 2013.
  
The classes and members used for external automation are exposed through the [Microsoft.Office.Interop.InfoPath](https://msdn.microsoft.com/library/microsoft.office.interop.infopath.aspx) and [Microsoft.Office.Interop.InfoPath.Xml](https://msdn.microsoft.com/en-us/library/microsoft.office.interop.infopath.xml) namespaces. The assembly files that are required for writing automation code are located in the C:\Program Files\Microsoft Office\Office14 folder. 
  
|**Assembly**|**Description**|
|:-----|:-----|
|Microsoft.Office.Interop.InfoPath.dll  <br/> |Provides COM interop against the InfoPath COM object model for external automation code written using C# or Visual Basic.  <br/> |
|Microsoft.Office.Interop.InfoPath.Xml.dll  <br/> |Provides COM interop against the MSXML for XML DOM operations in external automation code written using C# or Visual Basic.  <br/> |
   
For more information about the object models provided by the **Microsoft.Office.Interop.InfoPath** and **Microsoft.Office.Interop.InfoPath.Xml** namespaces, which are used exclusively to automate the InfoPath application by using managed code from external applications, see the [InfoPath Developer Center](http://msdn.microsoft.com/en-us/office/aa905434.aspx).
  
### The InfoPath Forms Services Object Model

The managed code object model for automating InfoPath Forms Services administration tasks is implemented in the Microsoft.Office.InfoPath.Server.dll which is located at \<drive\>:\Program Files\Microsoft Office Server\15.0\Bin on a Microsoft SharePoint Server 2013 installation.
  
|**Assembly**|**Description**|
|:-----|:-----|
|Microsoft.Office.InfoPath.Server.dll  <br/> |The object model for automating InfoPath Forms Services tasks such as uploading, activating, or deactivating browser-enabled form templates.  <br/> |
   
For more information about the InfoPath Forms Services object model, see the SharePoint Server 2013 Software Developers Kit (SDK) which is available on MSDN.
  
## InfoPath Development Environment

The development of business logic in InfoPath 2013 form templates can be performed by using Visual Studio 2012 with the [Microsoft Visual Studio Tools for Applications 2012](https://www.microsoft.com/en-us/download/details.aspx?id=38807) add-on installed. 
  
> [!NOTE]
> InfoPath 2013 does not support creating or editing form templates that use business logic written with JScript or VBScript, although the InfoPath Filler supports opening script-based form templates that were created in previous versions of InfoPath. 
  
## See also

- [Walkthrough: Creating a Basic Form Template with Code](walkthrough-creating-a-basic-form-template-with-code.md)
- [Walkthrough: Creating and Debugging a Basic Form Template Using the InfoPath 2003 Object Model](walkthrough-create-and-debug-basic-form-template-using-infopath-object-model.md)

