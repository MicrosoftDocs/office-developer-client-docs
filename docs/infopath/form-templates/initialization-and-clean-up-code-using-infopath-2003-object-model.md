---
title: "Initialization and Clean-up Code Using InfoPath 2003 Object Model"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- infopath 2003-compatible form templates, clean-up code,InfoPath 2003-compatible form templates, initialization code
 
ms.localizationpriority: medium
ms.assetid: 8d19e8fa-4e5c-40bb-ae89-7a552cc7914d
description: "By default, the FormCode.cs or FormCode.vb file that is created for a form template project that is compatible with InfoPath 2003 contains all the source code for the programming logic of the form. The template for the project generates a class in the FormCode.cs or FormCode.vb file much like the classes in the following examples where you can define initialization and clean-up code, as well as handlers for form events. The FormCode.cs and FormCode.vb files apply an assembly-level System.ComponentModel.DescriptionAttribute attribute, which identifies the class as the only class where event handlers are implemented. The InfoPathNamespace attribute (which is implemented by the InfoPathNamespaceAttribute type) is applied to a class to identify the XML DOM selection namespaces used within the class. The namespaces referenced in the InfoPathNamespace are maintained by the InfoPath project system."
---

# Initialization and Clean-up Code Using InfoPath 2003 Object Model

By default, the FormCode.cs or FormCode.vb file that is created for a form template project that is compatible with InfoPath 2003 contains all the source code for the programming logic of the form. The template for the project generates a class in the FormCode.cs or FormCode.vb file much like the classes in the following examples where you can define initialization and clean-up code, as well as handlers for form events. The FormCode.cs and FormCode.vb files apply an assembly-level **System.ComponentModel.DescriptionAttribute** attribute, which identifies the class as the only class where event handlers are implemented. The **InfoPathNamespace** attribute (which is implemented by the [InfoPathNamespaceAttribute](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.InfoPathNamespaceAttribute.aspx) type) is applied to a class to identify the XML DOM selection namespaces used within the class. The namespaces referenced in the **InfoPathNamespace** are maintained by the InfoPath project system. 
  
The FormCode class itself provides `_Startup` and `_Shutdown` methods that are used to perform initialization and clean-up routines for any components that are required in addition to standard InfoPath functionality while the form is open. 
  
> [!IMPORTANT]
> Do not call members of the InfoPath object model from within the `_Startup` and `_Shutdown` methods. You should initialize and call only members of external components in these methods. 
  
```cs
using System;
using Microsoft.Office.Interop.InfoPath.SemiTrust;
// Office integration attribute. Identifies the startup class for the form. Do not
// modify.
[assembly: System.ComponentModel.DescriptionAttribute(
    "InfoPathStartupClass, Version=1.0, Class=Template1.FormCode")]
namespace Template1
{
    // The namespace prefixes defined in this attribute must remain synchronized with
    // those in the form definition file (.xsf).
    [InfoPathNamespace(
        "xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2004-03-29T22-27-27'")]
    public partial class FormCode
    {
        private XDocument thisXDocument;
        private Application thisApplication;
        public void _Startup(Application app, XDocument doc)
        {
            thisXDocument = doc;
            thisApplication = app;
            // You can add additional initialization code here.
        }
        public void _Shutdown()
        {
        }
    }
}
```

```vb
Imports System
Imports Microsoft.Office.Interop.InfoPath.SemiTrust
Imports Microsoft.VisualBasic
' Office integration attribute. Identifies the startup class for the form. Do not
' modify.
<Assembly: System.ComponentModel.DescriptionAttribute( _
    "InfoPathStartupClass, Version=1.0, Class=Template1.FormCode")>
Namespace Template1
    ' The namespace prefixes defined in this attribute must remain synchronized with
    ' those in the form definition file (.xsf).
    <InfoPathNamespace( _
        "xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2004-03-29T22-36-40'")> _
    Public Class FormCode
        Private thisXDocument As XDocument
        Private thisApplication As Application
        Public Sub _Startup(app As Application, doc As XDocument)
            thisXDocument = doc
            thisApplication = app
            ' You can add additional initialization code here.
        End Sub
        Public Sub _Shutdown()
        End Sub
    End Class
End Namespace
```

## The _Startup Method

In addition to providing a place to write initialization code for additional components, the `_Startup` method initializes the `thisXDocument` and `thisApplication` variables that can be used in your form code to access the members of the [XDocument](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.XDocument.aspx) and [Application](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.Application.aspx) classes in the InfoPath object model. The code necessary to initialize the two variables is generated automatically by the project template. 
  
```cs
    private XDocument thisXDocument;
    private Application thisApplication;
    public void _Startup(Application app, XDocument doc)
    {
        thisXDocument = doc;
        thisApplication = app;
        // You can add additional initialization code here.
    }
```

```vb
    Private thisXDocument As XDocument
    Private thisApplication As Application
    Public Sub _Startup(app As Application, doc As XDocument)
        thisXDocument = doc
        thisApplication = app
        ' You can add additional initialization code here.
    End Sub

```

The following examples show a simple event handler for a button that uses the `thisXDocument` variable to access the [Alert](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UI2.Alert.aspx) method of the [UIObject](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.UIObject.aspx) type. 
  
```cs
[InfoPathEventHandler(MatchPath="CTRL1_5", EventType=InfoPathEventType.OnClick)]
public void CTRL1_5_OnClick(DocActionEvent e)
{
    // Write your code here.
    thisXDocument.UI.Alert("Hello!");
}
```

```vb
<InfoPathEventHandler(MatchPath:="CTRL1_5", EventType:=InfoPathEventType.OnClick)> _
Public Sub CTRL1_5_OnClick(ByVal e As DocActionEvent)
    ' Write your code here.
    thisXDocument.UI.Alert("Hello!")
End Sub
```

For information on how to create an event handler, see [Add an Event Handler Using the InfoPath 2003 Object Model](how-to-add-an-event-handler-using-the-infopath-2003-object-model.md).
  
## The _ShutDown Method

The `_Shutdown` method is the last method called when a form is closed. You can write any code in this method that is needed to clean up or finalize components used in the form. 
  
```cs
    public void _Shutdown()
    {
    }
```

```vb
    Public Sub _Shutdown()
    End    Sub
```

## Initialization and Clean-up Code Example

The following example shows how to initialize a connection to a Microsoft SQL Server database in the `_Startup` method and close the connection in the `_Shutdown` method. In order for this example to work correctly, you must first set a reference to the System.Data assembly of the .NET Framework by clicking **Add Reference** on the **Project** menu, and then selecting the System.Data.dll component on the **.NET** tab. Also note that the `using System.Data.SqlClient` (or `Imports System.Data.SqlClient)` directive was added at the top of the form code file to reduce keystrokes. 
  
> [!NOTE]
> Users of an InfoPath form that contains form code that connects to a SQL Server database may require security permissions depending on how the form is deployed and security policy is defined. For more information on security see [About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md) and [Configure Security Settings for Form Templates with Code](how-to-configure-security-settings-for-form-templates-with-code.md). 
  
```cs
using System;
using System.Data.SqlClient;
using Microsoft.Office.Interop.InfoPath.SemiTrust;
// Office integration attribute. Identifies the startup class for the form. Do not
// modify.
[assembly: System.ComponentModel.DescriptionAttribute(
    "InfoPathStartupClass, Version=1.0, Class=Template1.FormCode")]
namespace Template1
{
    // The namespace prefixes defined in this attribute must remain synchronized with
    // those in the form definition file (.xsf).
    [InfoPathNamespace(
        "xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2004-03-05T20-56-13'")]
    public partial class Template1
    {
        private XDocument    thisXDocument;
        private Application    thisApplication;
        private SqlConnection sqlConnect;
        public void _Startup(Application app, XDocument doc)
        {
            thisXDocument = doc;
            thisApplication = app;
            // Initialize variable for SQL Server connection.
            sqlConnect= new SqlConnection("server=localhost;Trusted_Connection=yes;database=Northwind");
        }
        public void _Shutdown()
        {
            // Close SQL Server connection at shut down.
            sqlConnect.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Data.SqlClient
Imports Microsoft.Office.Interop.InfoPath.SemiTrust
Imports Microsoft.VisualBasic
' Office integration attribute. Identifies the startup class for the form. Do not
' modify.
<Assembly: System.ComponentModel.DescriptionAttribute( _
    "InfoPathStartupClass, Version=1.0, Class=Template1.FormCode")>
Namespace Template1
        ' The namespace prefixes defined in this attribute must remain synchronized with
        ' those in the form definition file (.xsf).
        <InfoPathNamespace( _
            "xmlns:my='http://schemas.microsoft.com/office/infopath/2003/myXSD/2004-03-08T18-47-33'")>        _
        Public Class Template1
            Private thisXDocument As XDocument
            Private thisApplication As Application
            Private sqlConnect As SqlConnection
            Public Sub _Startup(app As Application, doc As XDocument)
                thisXDocument = doc
                thisApplication = app
                ' Initialize variable for SQL Server connection.
                sqlConnect = New SqlConnection _("server=localhost;Trusted_Connection=yes;database=Northwind")
            End Sub
        Public Sub _Shutdown()
            ' Close SQL Server connection.
            sqlConnect.Close()
        End Sub
    End Class
End Namespace
```

## See also



[Add an Event Handler Using the InfoPath 2003 Object Model](how-to-add-an-event-handler-using-the-infopath-2003-object-model.md)

