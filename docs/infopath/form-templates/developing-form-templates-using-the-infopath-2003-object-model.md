---
title: "Developing Form Templates Using the InfoPath 2003 Object Model"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- form templates [infopath 2007], using infopath 2003 object model,InfoPath 2003-compatible form templates,InfoPath 2007, developing form templates using InfoPath 2003 object model,object models [InfoPath 2003], developing managed code form templates
 
localization_priority: Normal
ms.assetid: c74cbcd0-4fe6-4eb7-a05c-f61e1868c42b
description: "Microsoft InfoPath continues to support form template projects created with Microsoft Office InfoPath 2003 Toolkit for Visual Studio .NET or Visual Studio 2005 Tools for the Microsoft Office System that have business logic written against members of the Microsoft.Office.Interop.InfoPath.SemiTrust namespace. The topics in this section refer to the types and members of this namespace as the InfoPath 2003-compatible object model or simply the InfoPath 2003 object model. InfoPath also supports form template projects created with Microsoft Office InfoPath 2007 that use the InfoPath 2003-compatible object model. In addition, you can use InfoPath to create new form template projects that use InfoPath 2003-compatible object model to retain backward compatibility for users of Office InfoPath 2007. All topics in this section are specific to creating and developing form templates that work with the InfoPath 2003-compatible object model provided by the Microsoft.Office.Interop.InfoPath.SemiTrust namespace."
---

# Developing Form Templates Using the InfoPath 2003 Object Model

Microsoft InfoPath continues to support form template projects created with Microsoft Office InfoPath 2003 Toolkit for Visual Studio .NET or Visual Studio 2005 Tools for the Microsoft Office System that have business logic written against members of the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace. The topics in this section refer to the types and members of this namespace as the InfoPath 2003-compatible object model or simply the InfoPath 2003 object model. InfoPath also supports form template projects created with Microsoft Office InfoPath 2007 that use the InfoPath 2003-compatible object model. In addition, you can use InfoPath to create new form template projects that use InfoPath 2003-compatible object model to retain backward compatibility for users of Office InfoPath 2007. All topics in this section are specific to creating and developing form templates that work with the InfoPath 2003-compatible object model provided by the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace. 
  
> [!IMPORTANT]
> Although creating business logic with the managed-code object model provided by the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace is still supported by InfoPath, business logic written using this object model it is not supported for browser-enabled form templates deployed to Microsoft SharePoint Server 2010 with InfoPath Forms Services. Browser-enabled form templates must use the new InfoPath managed code object model provided by members of the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace for custom business logic. For more information about creating form templates with business logic written with members of the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace, see [Developing InfoPath Form Templates with Code](developing-infopath-form-templates-with-code.md). > Also, note that users of form templates compiled with Visual Studio 2012 must have Microsoft .NET Framework 2.0 or later installed on their computers. Users of form templates compiled with Visual Studio .NET 2003 are only required to have Microsoft .NET Framework 1.1 on their computers. 
  
## In this section

[Getting Started Developing Form Templates Using the InfoPath 2003 Object Model](getting-started-developing-form-templates-using-the-infopath-2003-object-model.md)
  
> Provides information about how to start creating managed code form templates that work with the InfoPath 2003-compatible object model.
    
[Creating Form Templates Using the InfoPath 2003 Object Model](creating-form-templates-using-the-infopath-2003-object-model.md)
  
> Discusses initialization and clean-up code, how to add event handlers, how to debug and deploy managed-code form templates, threading support, and working with Microsoft XML Core Services (MSXML) from InfoPath managed-code solutions.
    
[Security in InfoPath Form Templates with Code](security-in-infopath-form-templates-with-code.md)
  
> Discusses the security model for InfoPath form templates that use managed code, debugging fully-trusted InfoPath form templates, and related security procedures.
    
[Understanding the InfoPath 2003 Object Model](understanding-the-infopath-2003-object-model.md)
  
> Discusses the InfoPath 2003-compatible object model, and common programming tasks for managed code form templates that work with that object model.
    
[Troubleshooting Form Templates That Use the InfoPath 2003 Object Model](troubleshooting-form-templates-that-use-the-infopath-2003-object-model.md)
  
> Contains tips for solving common problems that you might encounter when creating managed-code form templates that work with the InfoPath 2003-compatible object model.
    
## Related sections

[InfoPath Developer Portal](http://go.microsoft.com/fwlink?LinkID=11689)
  
> Contains links to technical articles, code samples, downloads, support, and other MSDN documentation on building custom InfoPath solutions.
    
[Microsoft Office Developer Center](http://go.microsoft.com/fwlink?LinkID=27128)
  
> Contains links to technical articles, code samples, downloads, support, and other MSDN documentation on building custom Office solutions.
    

