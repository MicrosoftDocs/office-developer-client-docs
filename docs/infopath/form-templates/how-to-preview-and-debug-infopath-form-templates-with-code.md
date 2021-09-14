---
title: "Preview and Debug InfoPath Form Templates with Code"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- previewing form templates [infopath 2007],debugging form templates [InfoPath 2007],form templates [InfoPath 2007], previewing,debugging [InfoPath 2007], managed-code form templates,form templates [InfoPath 2007], debugging,InfoPath 2007, debugging form templates,InfoPath 2007, previewing form templates
 
ms.localizationpriority: medium
ms.assetid: c8387f1c-b34c-490e-8bf9-d824bf98d826
description: "Microsoft InfoPath with Visual Studio 2012 enables debugging by running form code in preview mode. When you start debugging form code, your project is compiled and InfoPath displays your form in the InfoPath preview window. When a line of code that has a breakpoint set for it is encountered, the focus moves to the code editor. When you continue past a breakpoint, the focus moves back to the preview window. Debugging stops when you close the preview window."
---

# Preview and Debug InfoPath Form Templates with Code

Microsoft InfoPath with Visual Studio 2012 enables debugging by running form code in preview mode. When you start debugging form code, your project is compiled and InfoPath displays your form in the InfoPath preview window. When a line of code that has a breakpoint set for it is encountered, the focus moves to the code editor. When you continue past a breakpoint, the focus moves back to the preview window. Debugging stops when you close the preview window.
  
You can also modify the form options of the form template to preview and debug using a specific user role, a sample data file, or by specifying the domain to which the form will be published. 
  
> [!NOTE]
> It is not possible to debug form templates after they are deployed at run time from Visual Studio 2012. This includes form templates that are compatible only with InfoPath, as well as those that are compatible with InfoPath and the Web browser using InfoPath Forms Services. However, it is possible to log values to a field from code at run time to help with debugging a form template's business logic. For information about how to do that, see [Log Values to a Field for Debugging](how-to-log-values-to-a-field-for-debugging.md). 
  
## Debugging in Preview Mode

### To debug an InfoPath project in Preview Mode

1. Create or open an InfoPath managed code form template in Visual Studio 2012.
    
2. Set one or more breakpoints in your form code in the code editor by clicking the grey bar to the left of the line of code where you want to insert a breakpoint.
    
    A red circle is displayed and the line of code is highlighted to indicate that the runtime will pause at this breakpoint in your form code.
    
3. On the **Debug** menu, click **Start Debugging**; or press F5.
    
    The project will be compiled and the form is displayed in the preview window.
    
4. Interact with the form until a line of code containing a breakpoint is encountered.
    
    The focus returns to the code editor.
    
5. On the **Debug** menu, click **Continue**; or press F5.
    
6. When you are finished debugging, close the preview window; or on the **Debug** menu, click **Stop Debugging**.
    
> [!NOTE]
> To debug an InfoPath managed code form template when using an object model member that requires full trust, you must configure your form template as described in [Preview and Debug Form Templates that Require Full Trust](how-to-preview-and-debug-form-templates-that-require-full-trust.md). 
  
## Using a Sample Data File

By default, debugging and previewing uses the template.xml file that is created when a form template is created. You can create your own data file and specify to use it when previewing or debugging by using one of the following procedures. 
  
### To specify a sample data file to use while debugging or previewing in Visual Studio Tools for Applications

1. To view template.xml, open the form template in InfoPath design mode.
    
2. Click the **File** tab, click **Saving**, click **Save Form Template As**, and the click **Source Files**.
    
3. Save the form template files to a folder, and then open the template.xml file in a text editor.
    
4. Create and save a file with the same structure as template.xml with the sample data you want to use.
    
5. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
6. Click the **Preview** category of the **Form Options** dialog box, and then under **Sample data** specify the sample data file you created in the **File location** box. 
    
## Specifying a User Role to Use While Debugging or Previewing

If the form you are working with has user roles defined for it, you can specify a user role to use while debugging or previewing your form. For information on how to define user roles, search InfoPath help for "user role".
  
> [!NOTE]
> The option to specify a user role is not available if the compatibility setting for your form template is set to **Web Browser Form**. User roles are not supported in form templates opened in the browser from InfoPath Forms Services. 
  
### To specify a role to use while debugging or previewing

1. If you are working in Visual Studio 2012, switch to the InfoPath designer.
    
2. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
3. Click the **Preview** category of the **Form Options** dialog box, and then specify the user role to use in the **Preview as** drop-down box. 
    
## Specifying a Domain to Use While Debugging or Previewing

You can preview a form as if it was published to a specific domain. This setting will only apply if the security level of the form template is explicitly set to **Domain**.
  
### To specify a domain to use while debugging or previewing

1. If you are working in Visual Studio 2012, switch to the InfoPath designer.
    
2. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
3. Click the **Preview** category of the **Form Options** dialog box, and then specify the domain to use while previewing and debugging in the **Domain** box. 
    
4. Click the **Security and Trust** category of the **Forms Options** dialog box, clear the **Automatically determine security level** check box, and then click **Domain**.
    

