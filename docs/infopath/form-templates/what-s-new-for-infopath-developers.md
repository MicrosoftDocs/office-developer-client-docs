---
title: "What's New for InfoPath Developers"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- what's new [infopath 2007],developer features [InfoPath 2007],InfoPath 2007, what's new,new features [InfoPath 2007]
 
localization_priority: Normal
ms.assetid: d0ad3111-bd41-4f35-8a34-62c17f20fc19
description: "InfoPath is designed to make it easy to build rich forms-based applications on the Microsoft SharePoint Server platform. Microsoft InfoPath 2013 in conjunction with Microsoft SharePoint Server 2013 and InfoPath Forms Services have many features for developers. InfoPath Forms Services, which is available in SharePoint Server 2013, enables you to deploy an InfoPath form template to a SharePoint Server so that users without the InfoPath rich client can open and fill out InfoPath forms in a Web browser."
---

# What's New for InfoPath Developers

InfoPath is designed to make it easy to build rich forms-based applications on the Microsoft SharePoint Server platform. Microsoft InfoPath 2013 in conjunction with Microsoft SharePoint Server 2013 and InfoPath Forms Services have many features for developers. InfoPath Forms Services, which is available in SharePoint Server 2013, enables you to deploy an InfoPath form template to a SharePoint Server so that users without the InfoPath rich client can open and fill out InfoPath forms in a Web browser.
  
Form templates created using InfoPath 2013 continue to support business logic written against the classes and members of the **Microsoft.Office.InfoPath** namespace, which works the same way for a form opened in the InfoPath filler and in a form opened in a Web browser. By using business logic written to this managed object model, and by working with design checking features in InfoPath Designer, you can create a single form template that you can deploy to an appropriately configured document library on SharePoint Server 2013, which will run in both the InfoPath filler and in a Web browser. 
  
## New Features and Improvements

The following sections briefly describe these features and improvements that are interesting to InfoPath developers:
  
- New Way to Write and Edit Code
    
- SharePoint Sandboxed Solutions
    
- Publish Forms with One Click
    
- Enhance SharePoint List Forms
    
- Host Forms on Portal Pages using the InfoPath Form Web Part
    
- Richer Web Forms
    
- Standards Compliant Browser Forms
    
- Provide Enhanced Information Security and Integrity with Digital Signatures
    
- New Controls
    
## New Way to Write and Edit Code

The Microsoft Visual Studio Tools for Applications IDE that was integrated with InfoPath 2010 has been removed in InfoPath 2013. To write or edit form code in InfoPath 2013 now requires Visual Studio 2012 with the [Microsoft Visual Studio Tools for Applications 2012](http://www.microsoft.com/en-us/download/details.aspx?id=38807) add-on installed. The programming experience itself has not fundamentally changed, but you can now use the full Visual Studio development experience when writing managed code for your InfoPath forms. 
  
The following sections describe features that were first added in InfoPath 2010 and SharePoint Server 2010 and continue to add value for developers using InfoPath 2013 and SharePoint Server 2013.
  
## SharePoint Server Sandboxed Solutions

With InfoPath, it is easier than ever to deploy forms with code to SharePoint Server 2013. In Office InfoPath 2007, all forms with code had to be approved and uploaded by a SharePoint farm administrator. With support for sandboxed solutions in SharePoint Server 2013, form designers that have site collection administration permissions can now publish most forms with code, directly to their SharePoint sites. A resource quota setting on the server limits excessive resource usage. The site collection administrator remains in control and makes trust decisions about the solution. The farm administrator can be hands-off. For more information about publishing InfoPath form templates as sandboxed solutions, see [Publishing Forms with Code](publishing-forms-with-code.md).
  
## Publish Forms with One Click

InfoPath is designed to make it easier than ever to publish updates to your forms.. After the first time that you publish a form template, instead of clicking through several dialog boxes, you can complete this task with one click of the new **Quick Publish** button, which is available on the **Quick Access Toolbar**, and in the new Microsoft Office Backstage, which is available by clicking the **File** tab. 
  
## Enhance SharePoint List Forms

Using InfoPath, you can now extend and enhance the forms used for creating, editing and viewing items in a SharePoint list. By opening a list, clicking the **List** tab under **List Tools**, and then clicking **Customize Form**, you can auto generate an InfoPath form which resembles the default, out-of-the-box SharePoint list form. You can then customize and enhance this form by modifying the layout, creating additional views, and adding rules and data validation in InfoPath. When you are finished modifying your improved list form, you can publish it to SharePoint using the new one-click publish feature in InfoPath.
  
## Host Forms on Portal Pages using the InfoPath Form Web Part

In SharePoint Server 2013, it is easier than ever to host your forms on Web pages using the new **InfoPath Form Web Part**. In Microsoft Office SharePoint Server 2007, users who want host their InfoPath forms on Web pages have to write code in Visual Studio. Now, without writing a single line of code, you can add the **InfoPath Form Web Part** to a Web Parts page and point it to your published form.You can use the **InfoPath Form Web Part** to host any InfoPath browser form that is published to a SharePoint list or form library. You can also connect it to other Web Parts on the page to send or receive data. For more information about how to use the **InfoPath Form Web Part**, see [Working with the InfoPath Form Web Part](http://msdn.microsoft.com/library/bb87e126-1a07-45aa-af36-b294df3a2576%28Office.15%29.aspx) in the SharePoint 2010 SDK. 
  
## Richer Web Forms

The feature gap between client and browser forms has been narrowed, creating a more consistent form filling experience for all users. Controls and functionality that are now supported in browser forms include the following:
  
- Bulleted, numbered, and plain lists
    
- Multiple selection list boxes
    
- Combo boxes
    
- Picture buttons
    
- Hyperlink capabilities
    
- Choice group and section 
    
- Date and time controls
    
- Person/group pickers
    
- Filtering functionality
    
## Standards Compliant Browser Forms

InfoPath browser forms are now compliant with Web Content Accessibility Guidelines 2.0 (WCAG 2.0) AA, which enables form designers to create forms that are available for users with disabilities.
  
## Provide Enhanced Information Security and Integrity with Digital Signatures

InfoPath supports Cryptography Next Generation (CNG) digitally signed content. To help you ensure the integrity of the information that is contained in your forms, the InfoPath client and SharePoint Server 2013 provide the controls necessary to enable single, co-sign, and counter-sign scenarios for the full form or sections of the form. Forms can be signed in Internet Explorer using the ActiveX signature line control. Signed forms can be viewed in any browser supported by SharePoint Server 2013.
  
## New Controls

InfoPath provides a richer set of controls that can be added to your forms. The following list briefly describes some of the new controls:
  
- **Picture Button** — Instead of a gray rectangle; use any image as a button in your form. 
    
- **Hyperlink** — Enable users to enter their own hyperlinks when filling out forms. 
    
- **Person/Group Picker** — Enable users to check and query account names and groups when filling out forms. 
    
- **Entity Picker** — Enable users to select values from external lists on a server that is running SharePoint Server 2013 when forms. 
    
- **Signature Line** — Provide users with a signature line or stamp image, such as an inkan or hanko seal, when digitally signing forms. 
    
## See also

#### Other resources

[Developing InfoPath Form Templates with Code](developing-infopath-form-templates-with-code.md)
  
[Developing Form Templates Using the InfoPath 2003 Object Model](developing-form-templates-using-the-infopath-2003-object-model.md)

