---
title: Automation with Microsoft Access
TOCTitle: Automation with Microsoft Access
ms:assetid: 39fde349-3ba3-7c7a-3c92-316641dc8712
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff192643(v=office.15)
ms:contentKeyID: 48544258
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm13783
f1_categories:
- Office.Version=v15
---

# Automation with Microsoft Access


**Applies to**: Access 2013 | Office 2013

Microsoft Access is a COM component that supports Automation, formerly called OLE Automation. Microsoft Access supports Automation in two ways. From Microsoft Access, you can work with objects supplied by another component. Microsoft Access also supplies its objects to other COM components.

You can use the **New** keyword or the **CreateObject** method to create a new instance of a component. You can use the **GetObject** method to assign a variable to an existing instance of a component.

In Microsoft Access, you can set a reference to a component's type library to improve performance when you work with that component through Automation. Microsoft Access also includes the Object Browser, a tool that enables you to view objects in another component's type library, as well as their methods and properties.

The Microsoft Access type library provides information about Microsoft Access objects to other components. You can [set a reference](https://msdn.microsoft.com/en-us/library/ff194944\(v=office.15\)) to the Microsoft Access type library from a component and view its objects in the Object Browser.

To work with Microsoft Access objects through Automation, you must create an instance of the Microsoft Access **[Application](https://msdn.microsoft.com/en-us/library/ff821758\(v=office.15\))** object. For example, suppose you want to display data from Microsoft Excel in a Microsoft Access form or report. To launch Microsoft Access from Microsoft Excel, you can use the **New** keyword to create an instance of the Microsoft Access **Application** object. You can also use the **CreateObject** method to create a new instance of the Microsoft Access **Application** object, or you can use the **GetObject** method to point an object variable to an existing instance of Microsoft Access. Check your component's documentation to determine which syntax it supports.

Once you've launched an instance of Microsoft Access, if you want to control any Microsoft Access objects, you must open a database or project (.adp) in the Microsoft Access window by using either the **[OpenCurrentDatabase](https://msdn.microsoft.com/en-us/library/ff837226\(v=office.15\))** or the **[NewCurrentDatabase](https://msdn.microsoft.com/en-us/library/ff195271\(v=office.15\))** method for a database or by using the **[OpenAccessProject](https://msdn.microsoft.com/en-us/library/ff837249\(v=office.15\))** or the **[NewAccessProject](https://msdn.microsoft.com/en-us/library/ff835758\(v=office.15\))** method for a project.

If you've opened Microsoft Access only as a means of using the Data Access Objects provided by Microsoft DAO, then you don't need to open a database in the Microsoft Access window. You can use the **[DBEngine](https://msdn.microsoft.com/en-us/library/ff821724\(v=office.15\))** property of the Microsoft Access **Application** object to access objects in the Microsoft Office 12.0 Access Database Engine Object Library object library during an Automation operation.

