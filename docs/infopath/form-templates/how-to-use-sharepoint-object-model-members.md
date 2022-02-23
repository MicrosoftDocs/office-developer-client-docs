---
title: "Use SharePoint Object Model Members"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
ms.localizationpriority: medium
ms.assetid: 8cbafca3-7831-4231-8e61-38330b5ad61b
description: "Before you can program against members of the SharePoint object model from code running in an InfoPath form template, you must reference the Microsoft.SharePoint.dll assembly in the Visual Studio 2012 project for your form. To do that, you must have access to the file system of a licensed copy of Microsoft SharePoint Server 2010 or a server that is running Microsoft SharePoint Foundation 2010 so that you can obtain a copy of the Microsoft.SharePoint.dll assembly."
---

# Use SharePoint Object Model Members

Before you can program against members of the SharePoint object model from code running in an InfoPath form template, you must reference the Microsoft.SharePoint.dll assembly in the Visual Studio 2012 project for your form. To do that, you must have access to the file system of a licensed copy of Microsoft SharePoint Server 2010 or a server that is running Microsoft SharePoint Foundation 2010 so that you can obtain a copy of the Microsoft.SharePoint.dll assembly.
  
Additionally, your form template must be deployed to the server as either a sandboxed or administrator-approved solution. For more information about these deployment options, see [Publishing Forms with Code](publishing-forms-with-code.md).
  
## Add and Reference the Microsoft.SharePoint Assembly from an InfoPath Form Template

> [!IMPORTANT]
> To avoid a conflict with how the InfoPath project system manages files that are added to the form template file, do not copy any assemblies that you want to reference into the top-level folder of a form template project. By default, this will be a path in the following format: < *drive* >:\Users\ *UserName*  \Documents\InfoPath Projects\ *ProjectName* > If you do want to move assemblies that you reference to a location within the project folder, you must create a subfolder under the main *ProjectName*  project folder, and then copy and reference assemblies from that subfolder. However, be aware that creating a subfolder for referenced assemblies is not necessary. As long as a referenced assembly is not located within the project's top-level folder, the InfoPath project system will copy the assembly into the form template file (.xsn) when the project is compiled and published.
  
By default, Microsoft.SharePoint.Server.dll is installed in C:\Program Files\Common Files\Microsoft Shared\Web Server\Extensions\14\ISAPI in the file system of SharePoint Server 2010 or a server that is running SharePoint Foundation 2010.
  
### To reference the Microsoft.SharePoint assembly from an InfoPath form's code project

1. Copy the Microsoft.SharePoint.Server.dll assembly from the server to a local folder, or get access to the assembly from a shared folder.

2. Open the form template project in Visual Studio 2012.

3. On the **Project** menu, click **Add Reference**.

4. Click the **Browse** tab, locate and specify the assembly, and then click **OK** to add the reference.

Now you can write code against members of the SharePoint object model from your form code. To make it easier to reference members of the Microsoft.SharePoint namespace, add `using Microsoft.SharePoint;` or `Imports Microsoft.SharePoint` to the directives at the beginning of your code file. For an example that shows how to use members of the SharePoint object model in an InfoPath form, see "Example 2: Managing Vendors in a SharePoint List" in [Sample Sandboxed Solutions](sample-sandboxed-solutions.md).
