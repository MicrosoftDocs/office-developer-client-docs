---
title: "Deploy InfoPath Form Templates with Code"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- deploying form templates [infopath 2007],InfoPath 2007, deploying form templates,form templates [InfoPath 2007], deploying,.NET Framework security settings [InfoPath 2007],deployment [InfoPath 2007], form templates
 
ms.localizationpriority: medium
ms.assetid: ab66e26d-74ee-4211-b387-1385183a6803
description: "The form code for an InfoPath managed code form template is compiled as an assembly that runs under the common language runtime (CLR). This means that whenever you need to make changes to the form code, you must open its project in Visual Studio 2012, make changes in the code editor, recompile your form template, and then re-deploy the form template. Additionally, because the private assembly for a managed code form template is running under a hosted CLR application domain, the security settings for forms that require full trust differ somewhat from form templates that do not require full trust."
---

# Deploy InfoPath Form Templates with Code

The form code for an InfoPath managed code form template is compiled as an assembly that runs under the common language runtime (CLR). This means that whenever you need to make changes to the form code, you must open its project in Visual Studio 2012, make changes in the code editor, recompile your form template, and then re-deploy the form template. Additionally, because the private assembly for a managed code form template is running under a hosted CLR application domain, the security settings for forms that require full trust differ somewhat from form templates that do not require full trust.
  
## Deploying Form Templates That Do Not Require Full Trust

If the form code for your form template does not use InfoPath object model members that require full trust, and the form template does not use features that require full trust, you can publish your form template directly from InfoPath using the following procedure. For information about the InfoPath security model, see [About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md).
  
### Deploy a form template that does not require full trust

1. Create and debug your form template in Visual Studio 2012.
    
2. If you are working in the Visual Studio 2012 code editor, switch to InfoPath, click the **File** tab, and then click the button for the desired publishing location on the **Publish** tab. (If you have published the form template previously, you can click the **File** tab, and then click **Quick Publish** to republish the form template to the same location.) 
    
    The form template is compiled and the **Publishing Wizard** is launched. Follow the steps in the **Publishing Wizard** to deploy your form to the location of your choice. For more information about using the **Publishing Wizard**, search InfoPath Help for "Publish a form template".
    
## Deploying Form Templates That Require Full Trust

If the form code for your form template does use InfoPath object model members that require full trust, or the form template uses features that require full trust, you must digitally sign your form template (.xsn) file with a code signing certificate from a trusted publisher, which your users will be prompted to trust when they open the form. This will also make your form fully-trusted, and in turn grant the FullTrust permission set to your form code.
  
### Compile, publish, and digitally sign a form template

1. Create and debug your form template in Visual Studio 2012.
    
2. If you are working in the Visual Studio 2012 code editor, switch to InfoPath, click the **File** tab, and then click **Form Options**.
    
3. Click the **Security and Trust** category. 
    
4. Under **Security Level**, clear the **Automatically determine security level** check box, and then select **Full Trust**.
    
5. Under **Form Template Signature**, select **Sign this form template**, click **Select Certificate**, and then specify the code signing certificate with which to sign the form template.
    
6. Click **OK** twice to close the **Form Options** dialog box, and then save your changes. 
    
7. Click the **Publish** tab, and then click the button for the desired publishing location. 
    
8. The form template is compiled and the **Publishing Wizard** is launched. Follow the steps in the **Publishing Wizard** to deploy your form template. For more information about using the **Publishing Wizard** to deploy a form template that requires full trust, search InfoPath Help for "Publish a form template with full trust". 
    
 **Notes**
- To digitally sign a form, you must have an authenticated code signing certificate installed on your computer. To acquire such a certificate, you must contact a certification authority or your network administrator.
    
- If you need to make changes to the form after publishing, you must repeat the procedure and re-sign the form template. This is because altering the form invalidates the digital signature. During the development of a form that requires full trust permissions you can use the procedure described in [Preview and Debug Form Templates that Require Full Trust](how-to-preview-and-debug-form-templates-that-require-full-trust.md) to register the form template on your local computer. 
    
## Configuring .NET Framework Security Settings

For additional control over the permissions granted to managed code running in an InfoPath managed code form template, you can use the .NET Framework 2.0 Configuration utility to grant a particular permission set to your form code.
  
> [!IMPORTANT]
> Configuring .NET Framework security settings for an InfoPath managed code form template does not affect whether InfoPath object model members that require full trust are allowed to run. You must either digitally sign or register a form template as described earlier in this topic to enable calls to InfoPath object model members that require full trust. Configuring .NET Framework security settings apply only to calls to members of .NET Framework classes and managed components other than the InfoPath object model. 
  
### Compile, publish, and configure .NET security settings for a form template

1. Create and debug your form template in Visual Studio 2012.
    
2. If you are working in the Visual Studio 2012 code editor, switch to InfoPath, click the **File** tab, click **Publish**, and then click the button for the desired publishing location.
    
    The form template is compiled and the **Publishing Wizard** is launched. Follow the steps in the **Publishing Wizard** to deploy your form template. For more information about using the **Publishing Wizard**, search InfoPath Help for "Publish a form template".
    
3. Perform the procedure described in the "Assigning FullTrust to Forms at a Specific URL or UNC" section of the [Configure Security Settings for Form Templates with Code](how-to-configure-security-settings-for-form-templates-with-code.md)
    
## See also

#### Tasks

[Configure Security Settings for Form Templates with Code](how-to-configure-security-settings-for-form-templates-with-code.md)


[About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md)
  
[Preview and Debug Form Templates that Require Full Trust](how-to-preview-and-debug-form-templates-that-require-full-trust.md)

