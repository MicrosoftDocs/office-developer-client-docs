---
title: "Project client programming"

 
manager: soliver
ms.date: 8/10/2016
ms.audience: Developer
 
f1_keywords:
- object model
- Project object model
- Project VBA
- VBA
keywords:
- vba, project object model,Project, programmability,Programmability, Project VBA,Visual Basic for Applications, Project object model,VBA, object model,VBA,Visual Basic for Applications
 
localization_priority: Normal
ms.assetid: 0ad49ff6-8dff-4379-a52c-d292c53c2bc0
description: "The Project 2013 desktop client applications—Project Standard 2013 and Project Professional 2013—can be customized and extended by using VBA to write macros. You can use Visual Studio 2012 to customize the ribbon user interface and create complex add-ins. Office Add-ins enables a new extensibility model for task panes in Project that are built on a common Office 2013 platform. Project Standard 2013 and Project Professional 2013 can run general Office Add-ins and use task pane add-ins that are developed specifically for Project to integrate with SharePoint, other websites and web applications, and external data."
---

# Project client programming

The Project 2013 desktop client applications—Project Standard 2013 and Project Professional 2013—can be customized and extended by using VBA to write macros. You can use Visual Studio 2012 to customize the ribbon user interface and create complex add-ins. Office Add-ins enables a new extensibility model for task panes in Project that are built on a common Office 2013 platform. Project Standard 2013 and Project Professional 2013 can run general Office Add-ins and use task pane add-ins that are developed specifically for Project to integrate with SharePoint, other websites and web applications, and external data.
  
 **Moving to Visual Studio** VBA is useful for recording macros and developing relatively simple automation solutions. To develop task pane add-ins, add-ins, and more complex, secure, scalable, and easily deployed solutions, we recommend that you use Visual Studio 2012. The Microsoft .NET Framework 4.0 and the Project 2013 primary interop assembly provide many advantages for developing and deploying solutions that automate and integrate the Project 2013 desktop clients. 
  
> [!NOTE]
> You can use Visual Studio 2010 to develop Project add-ins. However, Visual Studio 2012 includes templates and extensions that are designed to create Office Add-ins clients. 
  
The **MSProject** object model for VBA in Project 2013 is essentially the same as the **Microsoft.Office.Interop.MSProject** object model for managed-code solutions with Office Developer Tools for Visual Studio 2013 (also known as VSTO). Visual Studio 2012 includes templates for developing application-level add-ins for Project 2010 and for Project 2013 (either the Project Standard or Project Professional versions). VSTO and Office Developer Tools for Visual Studio 2012 simplify developing, testing, and deploying advanced integration solutions that can use the Project desktop client and other Office 2013 applications, and integrate with SharePoint sites, lists, and workflows. 
  
Task pane add-ins and other add-ins for Office and SharePoint can be sold in the Office Store (see [http://office.microsoft.com/store/](http://office.microsoft.com/en-us/store/)) for use with both Project Online and on-premises installations. VBA macros and VSTO add-ins cannot be distributed in the Office Store; they are designed for local use with Project Standard and Project Professional. You can distribute VBA macros within a project .MPP file, install them in the Global.MPT file on your computer, or distribute them in the enterprise global template in Project Server 2013. VSTO add-ins can be distributed more securely through [ClickOnce](http://msdn.microsoft.com/en-us/library/t71a733d.aspx) deployment, which enables easy updates. 
  
## Reference

[Project VBA developer reference](http://msdn.microsoft.com/en-us/library/ee861523%28office.15%29.aspx) Contains introductory and VBA Help articles. 
  
## Related sections

[Project Server 2013 architecture](project-server-2013-architecture.md) Shows how the Project clients interact with Project Server. 
  
## See also

#### Other resources

[Project for developers](http://msdn.microsoft.com/en-us/office/aa905469)
  
[Office developer center](https://dev.office.com)
  
[Visual Studio developer center](http://msdn.microsoft.com/en-us/vstudio/aa718325.aspx)
  
[ClickOnce Security and Deployment](http://msdn.microsoft.com/en-us/library/t71a733d.aspx)
  
[Available fields reference](http://office.microsoft.com/en-us/project-help/available-fields-reference-HA102749299.aspx?CTT=1)

