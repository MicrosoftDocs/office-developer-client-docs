---
title: "Understanding Fully Trusted Forms"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 64d62990-6275-edef-c639-b6ba8d10c38c
description: "InfoPath provides the ability to create fully trusted forms, which are forms that have greater security permissions and can access system resources and other components on a user's computer. This article describes what a fully trusted form is, and why it is used, and create a fully trusted form by manually converting and registering a standard form, or by digitally signing a standard form."
---

# Understanding Fully Trusted Forms

InfoPath provides the ability to create fully trusted forms, which are forms that have greater security permissions and can access system resources and other components on a user's computer. This article describes what a fully trusted form is, and why it is used, and create a fully trusted form by manually converting and registering a standard form, or by digitally signing a standard form.

InfoPath form templates can be deployed with varying levels of security. The level you use is dictated by the level of access to external resources that you want a form to have. By default, InfoPath form templates are restricted from accessing system resources and are not allowed to use any software components that are not marked as safe for scripting. However, this behavior can be overridden so that a form can access system resources and other external resources, including software components that are not marked as safe for scripting.
  
For a form to be used, InfoPath must be able to access the form template that the form is based on. When you create a form template, InfoPath creates an entry in the form definition (.xsf) file that contains the URL of the location of the form template. A URL-based form is said to be *sandboxed*. When a user fills it out, the form is added in a local cache and denied access to system resources. This kind of form inherits its permissions from the domain in which it is opened. 
  
However, you can modify a form so that it is based on a Uniform Resource Name (URN) instead, which allows access to system resources. Forms of this kind are said to be *fully trusted*. 
  
## Why Use a Fully Trusted Form?

Fully trusted forms have a better set of permissions than sandboxed forms. For example, they can contain programming code that uses external objects for accessing system resources, they can use software components or Microsoft ActiveX controls that are not marked as safe for scripting, and they can use custom business logic provided by .NET assemblies.
  
In addition, some members of the InfoPath object model are set to security level 3, which means that they can only be used in a fully trusted form. For example, to access the Microsoft Office **CommandBars** object, you use the [CommandBars](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.CommandBars.aspx) property of the InfoPath [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) class to set a reference to it. Because this property is set to security level 3, it cannot be used in a form that is not fully trusted. 
  
> [!NOTE]
> Using the [CommandBars](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.CommandBars.aspx) property of the [Window](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.Window.aspx) class, or any other object model member that has a security level of 3, in a form that is not fully trusted will result in a "permission denied" error. 
  
## What Makes a Form Fully Trusted?

The following actions, involving both the InfoPath user interface and the form files, are required to create and use a fully trusted form:
  
- Enabling InfoPath to allow for the use of fully trusted forms on the **Trusted Publishers** category of the **Trust Center** dialog box. This option must be enabled for users to open fully trusted forms. 
    
- Registering the fully trusted form on the target computer by using the **RegisterSolution** method of the InfoPath **Application** object. 
    
## Creating a Fully Trusted Form

- You can create the form manually, which involves modifying some of the form files directly.
    
- You can digitally sign the form template.
    
### Manually Creating a Fully Trusted Form

#### To manually create a fully trusted form

1. Make a backup copy of the form template that you want to make fully trusted.
    
2. Open the form template in InfoPath.
    
3. Save the form source files to a folder on your hard disk by clicking the **File** tab, clicking **Publish**, and then clicking **Export Source Files**.
    
4. Specify the folder in which to save the form source files, click **OK**, and then exit the InfoPath designer.
    
5. In the folder in which you extracted the form files, open the form definition (.xsf) file, named  `manifest.xsf` by default, in a text editor such as Microsoft Notepad. 
    
6. Add the following attributes to the **xDocumentClass** element in the .xsf file: 
   
   `requireFullTrust="yes"`<br/>
   `name="urn:MyForm:MyCompany`

   > [!NOTE]
   > The values that are used for the URN can be any kind of string value, as long as this value is unique. There must be at least two values after the `urn:` prefix, and these values must be separated by a colon. In addition, the URN should not exceed 255 characters. 
  
7. Save and close the .xsf file, and then open the XML template (.xml) file that is named  `Template.xml` by default, in a text editor such as Notepad. 
    
8. Remove the **href** attribute from the  `mso-infoPathSolution` processing instruction and replace it with the same **name** attribute that you used in step 6 for the .xsf file. 
    
   > [!NOTE]
   > The URN values that are used for the **name** attribute must be the same in both the .xsf file and XML template file. 
  
9. Save and close the XML template file.
    
10. Repackage the files into the .xsn CAB format with a tool such as makecab.exe.
    
    > [!NOTE]
    > Although InfoPath form designer supports repackaging the form files into an .xsn file, doing this will revert the form to a URL-based form. For this reason, you must repackage the files manually to avoid overwriting your changes to the form files. 
  
11. Create a custom installation program by using the **RegisterSolution** method of the InfoPath **Application** object to install the fully trusted form. A simple way to do this is to create a script file that uses the following lines of code (in either Microsoft JScript or VBScript syntax): 
    
    ```js
        objIPApp = new ActiveXObject("InfoPath.Application"); 
        objIPApp.RegisterSolution("C:\\MyForms\\MyTrustedForm.xsn"); 
        objIPApp.Quit(); 
        objIPApp = null;
    ```
   
    ```vb
        Public Sub InstallForm()
            Dim objIPApp As Object
            ' Create a reference to the Application object.
            Set objIPApp = CreateObject("InfoPath.Application")
            ' Register the InfoPath form template.
            objIPApp.RegisterSolution ("C:\\My Forms\\MyFormTemplate.xsn")
            MsgBox "The InfoPath form template has been registered."
            Set objIPApp = Nothing
        End Sub
        
    ```

> [!NOTE] 
> Although this example uses a simple script file, you can also use a more robust installation mechanism such as Microsoft Windows Installer (.msi) files. Be sure, however, to use the **RegisterSolution** method to correctly install the fully trusted form on the target computer. To access the **RegisterSolution** method of the InfoPath the **Application** object from Visual Basic or Visual Studio, set a reference to the Microsoft InfoPath 3.0 Type Library, which is provided by IPEDITOR.dll that is installed in the C:\Program Files\Microsoft Office\Office14 folder. 
  
If you have to remove a fully trusted form, you can use the **UnregisterSolution** method of the **Application** object as shown in the following JScript and VBScript examples. 
    
```js
    objIPApp = new ActiveXObject("InfoPath.Application"); 
    objIPApp.UnregisterSolution("C:\\MyForms\\MyTrustedForm.xsn"); 
    objIPApp.Quit(); 
    objIPApp = null;
```

```vb
    Public Sub UninstallForm()
        Dim objIPApp As Object
        ' Create a reference to the Application object.
        Set objIPApp = CreateObject("InfoPath.Application")
        ' Unregister the InfoPath form template.
        objIPApp.UnregisterSolution ("C:\My Forms\MyFormTemplate.xsn")
        MsgBox ("The InfoPath form template has been unregistered.")
        Set objIPApp = Nothing
    End Sub
    
```

### Digitally Signing a Form Template to Create a Fully Trusted Form

Digitally signing a form template enables you to deploy a fully trusted form template by email or on a Web server, such as a server that is running Microsoft SharePoint Foundation. Use the steps in the following three procedures to make a form fully trusted by specifying full trust for the form, signing it digitally, and then publishing it.
  
#### To digitally sign a form template

1. Open the form in the InfoPath designer, click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
2. In the **Form Options** dialog box, click the **Security and Trust** category. 
    
3. Clear the selection for **Automatically determine security level (recommended)**.
    
4. Select **Full Trust (the form has access to files and settings on the user's computer)**.
    
5. Under **Form Template Signature**, select **Sign this form template**.
    
6. Click **Select Certificate** to select a certificate that was previously downloaded and installed from a trusted certificate provider. 
    
7. Click OK two times to exit completely.
    
#### To publish the form template to a SharePoint Document Library

1. Click the **File** tab, click **Publish**, and then click **SharePoint Server**.
    
2. Follow the instructions in the **Publishing Wizard** to publish the form template to a new or existing SharePoint document library. 
    
#### To a create a form that is based on your fully trusted, digitally signed form template

1. In the SharePoint document library, click **Fill Out the Form**.
    
   > [!NOTE]
   > After publishing the form template to a SharePoint document library using the **Publishing Wizard**, the template is not displayed as an item in the form library. When you create a form in that document library, the template will be used by default as the template for the new form. 
  
2. If the default form template was digitally signed, InfoPath displays a security warning about the digitally signed form template. Select **Always trust files from this publisher and open them automatically**, and then click **Open**.
    
## Using a Fully Trusted Form

Using a fully trusted form is very similar to using a standard form. The only significant differences are that the form can access restricted resources and warnings will no longer be displayed.
  
> [!NOTE]
> To enable InfoPath to use a fully trusted form, users must ensure that the **Allow fully trusted forms to run on my computer** check box is selected on the **Trusted Publishers** category of the **Trust Center** dialog box. To open the **Trust Center** dialog box, click the **File** tab, click **Options** (below the **InfoPath** tab), click **Trust Center**, and then click **Trust Center Settings**. 
  
A fully trusted form can be opened in InfoPath from the **Fill Out a Form** dialog box. 
  
The **Fill Out a Form** dialog box opens when you click **More Forms** in the **Fill Out a Form** task pane, or you click **Fill Out a Form** on the **File** menu. 
  
### Making Changes to a Fully Trusted Form

If you only have to make changes to the .xsn file, you can have users replace their existing .xsn file with the new one after the changes are made. They will not have to reinstall it by using a custom installation program.
  
However, if you are making changes to the form files that the .xsn file contains, you must repackage the files, as explained earlier, and then have users reinstall the fully trusted form.
  
> [!NOTE]
> The best approach is to save the form template back to the .xsn format from the InfoPath designer, and then follow the steps in this article to create a fully trusted form. 
  
## Conclusion

Depending on your business requirements and the needs of your users, you may have to create a form that has a higher set of permissions than the standard InfoPath form. InfoPath provides the ability to modify a form so that it can access system resources and other external resources that are not marked as safe for scripting. This can be done manually by making modifications to the form files that a form template contains and running an installation script, or by digitally signing the form template.
  

