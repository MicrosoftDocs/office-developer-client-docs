---
title: "About Form Template Components"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
 
 
ms.localizationpriority: medium
ms.assetid: b51361fe-cf29-f890-9876-5aebe15c73e1
description: "Microsoft InfoPath form templates are composed of several files and components that are combined to provide specific functionality for a particular end user scenario or business need. InfoPath forms can vary in complexity depending on the type of need that they address."
---

# About Form Template Components

Microsoft InfoPath form templates are composed of several files and components that are combined to provide specific functionality for a particular end user scenario or business need. InfoPath forms can vary in complexity depending on the type of need that they address.
  
An InfoPath form template is essentially a type of application that creates a specified class of XML documents, defines their layout and editing behavior, enforces their data consistency, and provides the routing information that indicates where they should be stored.
  
It is important to understand that InfoPath form templates are composed of several different files of many different types; these files are collectively known as the form files. Usually, an InfoPath form template is composed of the following types of files.
  
|**Name**|**Extension**|**Description**|
|:-----|:-----|:-----|
|Form definition  <br/> |.xsf  <br/> |An InfoPath-generated file that contains information about all of the other files and components used in a form. This file serves as the manifest for the form. |
|XML Schema  <br/> |.xsd  <br/> |The XML Schema files that are used to constrain and validate a form's underlying XML document files. |
|View  <br/> |.xsl  <br/> |The presentation logic files that are used to present, view, and transform the data contained in a form's underlying XML document files. |
|XML template  <br/> |.xml  <br/> |The .xml file that contains the default data that is displayed in a view when a new form is created. |
|Presentation  <br/> |.htm, .gif, .bmp, and others  <br/> |The files that are used together with the view files to create a custom user interface. |
|Business logic  <br/> |.dll  <br/> |The compiled programming code used to implement specific editing behavior, data validation, event handlers, control of data flow, and other custom business logic. InfoPath business logic can be written in the Visual Basic and C# .NET programming languages, which are compiled and included as binary files. |
|Binary  <br/> |.dll, .exe  <br/> | Any custom components that provide additional business logic. |
|Form template  <br/> |.xsn  <br/> |The compressed file format (.cab) that packages all the form files into one file. |
   

