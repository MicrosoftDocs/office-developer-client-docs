---
title: "Open or Convert a Form Template Created with the InfoPath Toolkit"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- converting form templates [infopath 2007],InfoPath Toolkit, opening form templates from,form templates [InfoPath 2007], opening,InfoPath 2007, converting InfoPath Toolkit form templates,opening form templates [InfoPath 2007],form templates [InfoPath 2007], converting,script [InfoPath 2007], converting to managed code
 
localization_priority: Normal
ms.assetid: af8eca2e-ba9a-4c37-94af-662815fff518
description: "If you created an InfoPath 2003 managed code form template using one of the InfoPath 2003 Toolkits for Visual Studio and want to maintain compatibility with InfoPath 2003, you can continue to work on and further develop your form template project by opening it in Microsoft InfoPath and Visual Studio 2012."
---

# Open or Convert a Form Template Created with the InfoPath Toolkit

If you created an InfoPath 2003 managed code form template using one of the InfoPath 2003 Toolkits for Visual Studio and want to maintain compatibility with InfoPath 2003, you can continue to work on and further develop your form template project by opening it in Microsoft InfoPath and Visual Studio 2012.
  
Alternatively, you can migrate and upgrade the code in your InfoPath 2003 project to use the new .NET object model provided by the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace. When doing so, all of your code will need to be re-written to use members of the **Microsoft.Office.InfoPath** namespace, but all of the code from your previous project is retained and surrounded by **#if InfoPathManagedObjectModel** and **#endif** (C#) or **#If InfoPathManagedObject Model** and **#End If** (Visual Basic) statements for your reference. 
  
The following procedures describe how to open a managed code form template created by using the InfoPath Toolkit and maintain compatibility with InfoPath 2003 or migrate and upgrade to the new InfoPath object model. 
  
### Open a managed code form template created with the InfoPath Toolkit and maintain compatibility with InfoPath 2003 using Visual Studio Tools for Applications

1. Open the InfoPath Designer, and then click **Open** on the **File** tab. 
    
2. In the **Open in Design Mode** dialog box, navigate to the project folder where the InfoPath Toolkit form template project is saved. 
    
    By default, this will be a folder in  `C:\Users\` *username*  `\Documents\Visual Studio Projects` on the computer where the project was created. Or, you can move the folder to the location where InfoPath stores Visual Studio 2012 projects, which by default is  `C:\Users\` *username*  `\Documents\InfoPath Projects`
    
3. Click the file that is named manifest.xsf, and then click **Open**.
    
4. On the **Developer** tab, click **Code Editor**.
    
5. The message "This form template must be saved before you can add Visual Basic or C# code to it" is displayed. Click **OK** to continue. 
    
6. Navigate to the location where you want to save the file, name the file, and then click **Save**.
    
7. The message "This code was created with one of the InfoPath 2003 Toolkits for Microsoft Visual Studio. InfoPath needs to migrate the toolkit project to a new format" is displayed. Click **OK** to continue. 
    
8. Select the Visual Studio Solution (.sln) file for the project, and then click **Open**.
    
9. The message "Your project has been migrated" is displayed when the migration process is complete. Click **OK** to continue. 
    
10. The message "The code in this form uses the InfoPath 2003 object model" is displayed with the prompt "Do you want to upgrade your code to use the Microsoft Office InfoPath object model?" Click **No** to retain compatibility with InfoPath 2003 and to continue working with the object model provided by the [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespace. 
    
    For information about how to work with managed code form templates that are compatible with InfoPath 2003, see [Developing Form Templates Using the InfoPath 2003 Object Model](developing-form-templates-using-the-infopath-2003-object-model.md).
    
### Open a managed code form template created with the InfoPath Toolkit and upgrade it to use the new InfoPath object model using Visual Studio Tools for Applications

1. Open the InfoPath Designer, and then click **Open** on the **File** tab. 
    
2. Under **Open a form template**, click **On My Computer**.
    
3. In the **Open in Design Mode** dialog box, navigate to the project folder where the InfoPath Toolkit form template project is saved. 
    
    By default this will be a folder in  `C:\Users\` *username*  `\Documents\Visual Studio Projects` on the computer where the project was created. Or, you can move the folder to the location where InfoPath stores Visual Studio 2012 projects, which by default is  `C:\Users\` *username*  `\Documents\InfoPath Projects`
    
4. Click the file that is named manifest.xsf, and then click **Open**.
    
5. On the **Developer** tab, click **Code Editor**.
    
6. The message "This form template must be saved before you can add Visual Basic or C# code to it" is displayed. Click **OK** to continue. 
    
7. Navigate to the location where you want to save the file, name the file, and then click **Save**.
    
8. The message "This code was created with one of the InfoPath 2003 Toolkits for Microsoft Visual Studio. InfoPath needs to migrate the toolkit project to a new format" is displayed. Click **OK** to continue. 
    
9. Select the Visual Studio Solution (.sln) file for the project, and then click **Open**.
    
10. The message "Your project has been migrated" is displayed when the migration process is complete. Click **OK** to continue. 
    
11. The message "The code in this form uses the InfoPath 2003 object model" is displayed with the prompt "Do you want to upgrade your code to use the Microsoft Office InfoPath object model?" Click **Yes** to upgrade the form template to use the new managed code object model provided by the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) namespace. 
    
    Your form code is opened in the Visual Studio 2012 code editor with all of the code from your previous project surrounded by **#if** **InfoPathManagedObjectModel** and **#endif** (C#) or **#If InfoPathManagedObjectModel** and **#End If** (Visual Basic) statements for your reference. All of this code will have to be re-written to use members of the object model provided by the **Microsoft.Office.InfoPath** namespace. 
    
    For information about how to work with managed code form templates that use the new InfoPath managed code object model, see [Developing InfoPath Form Templates with Code](developing-infopath-form-templates-with-code.md).
    

