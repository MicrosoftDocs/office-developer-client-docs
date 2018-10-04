---
title: "Develop with Visual Studio"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: e39d633d-d8fb-4e2f-a396-6cb50beb8c3e
description: "You can greatly enhance the functionality of your InfoPath forms by extending them with managed code developed in Visual Studio 2012. You can then publish your forms with code to form libraries on SharePoint Server 2013."
---

# Develop with Visual Studio

You can greatly enhance the functionality of your InfoPath forms by extending them with managed code developed in Visual Studio 2012. You can then publish your forms with code to form libraries on SharePoint Server 2013.
  
You can start programming and deploying your InfoPath forms with managed code in three high-level steps:
  
1. Install Visual Studio 2012 with the [Microsoft Visual Studio Tools for Applications 2012](https://www.microsoft.com/en-us/download/details.aspx?id=38807) add-on. 
    
2. Set your programming language, and then write and debug code in the Visual Studio 2012 code editor.
    
3. When you have finished designing the form and developing your code, the form template can be published to SharePoint Server 2013.
    
Here are some reasons to consider creating forms that are compatible with SharePoint Server 2013:
  
- Forms deployed to SharePoint Server 2013 with InfoPath Forms Services can be filled out in a browser. This enables users who do not have InfoPath installed to open and use your forms.
    
- You design only one version of the form. Forms that are compatible with Microsoft SharePoint Server are also compatible with the InfoPath Filler, but forms that are compatible only with the InfoPath Filler cannot be opened in the browser.
    
There are two ways to publish your form to SharePoint: SharePoint sandboxed solutions, and administrator-deployed solutions. For more information about each publication method and suggestions about which method is best for your scenario, see [Publishing Forms with Code](publishing-forms-with-code.md). For example solutions for sandboxed solutions, see [Sample Sandboxed Solutions](sample-sandboxed-solutions.md).
  
## Developing with Visual Studio

With Visual Studio 2012 and the Microsoft Visual Studio Tools for Applications 2012 add-on installed, you are ready to start to develop InfoPath managed code solutions.
  
### Choosing a Programming Language

InfoPath provides the options to program by using four versions of the InfoPath object model in two languages: Visual Basic and C#. The four versions of the object model provide compatibility with InfoPath 2013, InfoPath, Office InfoPath 2007, and Microsoft InfoPath 2003.
  
### To specify the programming language and object model

1. With a form template project open in the InfoPath designer, click **Language** on the **Developer** tab. 
    
2. In the **Programming** category of the **Form Options** dialog box, select the language that you want to work with from the **Form template code language** drop-down list. Then, select the version of the object model from the **Target version** drop-down list. The **Target version** option that is compatible only with InfoPath 2013 does not have a version year following the **InfoPath** name. 
    
    > [!NOTE]
    > Not all form template types support code. For example, the **SharePoint List** form template type and **Template Parts** do not support form code. When designing a form template type that does not support code, the **Developer** tab will not be available. Also, only some form template types support all four versions of the object model. For example, the **Blank Form (InfoPath Filler)** template type supports all four versions of the object model (and creates form template that are compatible only with the InfoPath Filler in those versions), but the **Blank Form** template supports only InfoPath 2013 and InfoPath (and creates form templates that are compatible with both the InfoPath Filler and the browser). 
  
    You can set a default programming language so that the InfoPath form designer will always start with the language and object model version of your choice.
    
### To set the default programming language

1. Click the **File** tab, and then click **Options**.
    
2. In the **General** section of the **InfoPath Options** dialog box, click **More Options**.
    
3. On the **Design** tab of the **Options** dialog box, select the default programming language in the **Programming Defaults** section. 
    
### Writing Code

You can now start to develop with InfoPath 2013 and Visual Studio 2012. 
  
### To start the Visual Studio Code Editor

1. Open a form template in the InfoPath designer.
    
2. Click **Code Editor** on the **Developer** tab. 
    
> [!TIP]
> You can also start the code editor and automatically add event handlers for form and control events using commands on the **Developer** tab, context menus, and other user interface methods. For more information, see [Add an Event Handler](how-to-add-an-event-handler.md)
  

