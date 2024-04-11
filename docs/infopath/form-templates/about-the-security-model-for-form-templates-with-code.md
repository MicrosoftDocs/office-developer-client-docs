---
title: "About the Security Model for Form Templates with Code"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
keywords:
- infopath 2007, security,code access security [InfoPath 2007],security [InfoPath 2007], security model for managed code,security [InfoPath 2007], levels,CAS [InfoPath 2007],InfoPath 2003-compatible form templates, security,permissions [InfoPath 2007]
ms.localizationpriority: medium
ms.assetid: 5e1c1c72-f98d-4871-9c57-82c315277aa1
description: "InfoPath managed code form templates support the same security levels as script running in unmanaged form templates, and they also support additional code access security features that apply to managed code running under the common language runtime (CLR) of the .NET Framework."
---

# About the Security Model for Form Templates with Code

InfoPath managed code form templates support the same security levels as script running in unmanaged form templates, and they also support additional code access security features that apply to managed code running under the common language runtime (CLR) of the .NET Framework.
  
## InfoPath Managed Object Model Security Levels

The following table describes the relationship between the security levels for script object model members and the corresponding permission set that is demanded for each level when the object model member is used in a managed code form template.
  
|**Object Model Security Level**|**Description**|**Permission Set Demanded**|
|:-----|:-----|:-----|
|0  <br/> |Can be accessed without restrictions. |None  <br/> |
|2  <br/> |Can be accessed only by forms running in the same domain as the currently open form, or by forms that have been granted cross-domain permissions. |None  <br/> |
|3  <br/> |Can be accessed only by fully trusted forms. |FullTrust  <br/> |
   
> [!NOTE]
> The security level "1" is not used by the current InfoPath COM server and is reserved for future use. 
  
> [!IMPORTANT]
> Even though object model levels 0 and 2 do not demand any permission set, because they contain managed code, they behave as defined for the Domain domain access security level that is described in the following section. 
  
The security level of each object model member exposed by the Microsoft.Office.InfoPath and Microsoft.Office.Interop.InfoPath.SemiTrust assemblies is specified in the Remarks section of the topic that documents that member in the [Microsoft.Office.InfoPath](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.aspx) and [Microsoft.Office.Interop.InfoPath.SemiTrust](https://msdn.microsoft.com/library/Microsoft.Office.Interop.InfoPath.SemiTrust.aspx) namespaces. 
  
## InfoPath Domain Access Security Levels

In conjunction with the object model security levels that are enforced by the COM server exposed by the InfoPath application, InfoPath defines three security levels that are applied depending on where the form template is located, how the form is deployed, and settings configured in design mode. These three security levels are defined in the following table.
  
|**Domain Access Security Level**|**Description**|
|:-----|:-----|
|Restricted  <br/> |Does not permit any communication outside of the form template. This security level is intended to prevent harmful forms from transmitting any data from your computer to a malicious attacker. When running in this security mode, the following features will not work: Custom Task Pane, Data Connections (except email submit), ActiveX controls, managed code form code, Roles, and Workflow. Managed code form templates cannot run in the Restricted domain. When a managed code form template is set to the **Automatically determine security level** setting in the **Security and Trust** category of the **Form Options** dialog box, the form template will always require at least the Domain security access level to run code.<br/>**IMPORTANT**: The managed code assembly created for a managed code form template will not load and run when a form is opened from a Restricted domain, for example, from an InfoPath form sent as an email attachment. Any form template you wish to deploy as an email attachment must omit the features listed above, and if the form template contains form code, form code must be implemented in JScript or VBScript, and must only utilize object model members with a security level of 0 (zero).           |
|Domain  <br/> |Restricts a form based on its location in one of the security zones defined by Microsoft Internet Explorer. For example, if the form is located in the Local Intranet zone, it is allowed to communicate with other data inside its own domain but it is not permitted to retrieve data from other domains. The location in a Microsoft Internet Explorer security zone also determines whether ActiveX controls that are marked as unsafe for scripting will be allowed to run. |
|Full Trust  <br/> |Allows you to run a form with full trust on the computer where the form will be used. This security level can only be used when working with a form that is digitally signed with a signature that matches a trusted root publisher on your computer, or by creating an installation program that installs the form and sets the **requireFullTrust** attribute of the **xDocumentClass** element to "yes" in the form definition file (.xsf). By using this setting, your form can access object model calls that require object model security level 3, such as properties and methods that access the file system, and you can disable certain security prompts that appear when running at a more restrictive security level. |
   
By default, an InfoPath form is configured to select automatically either the Restricted or Domain security level depending on the features that are being used in the form template, and where and how the form template is deployed. For example, a form template deployed as an email attachment is automatically configured to the Restricted security level. The security setting is always as restrictive as possible, starting at Restricted, to ensure a greater level of protection for you and your data. When a form template that contains managed code is set to automatically select the security level, the form template will always require at least the Domain security access level before code can run. You can manually override this setting at design time to select a level of security that is more appropriate for the form by using the following procedure. 
  
### Specify a form's security level

1. Open the form in the InfoPath form designer, click the **File** tab, click **Info**, and then click **Form Options**.
    
2. In the **Form Options** dialog box, click the **Security and Trust** category. 
    
3. Clear the **Automatically determine security level (recommended)** check box. 
    
4. Select the desired security level.
    
> [!NOTE] 
> - If you the select the **Restricted** security level for a managed code form template, the code behind the form will not load and run regardless of which object model members are used in the form code. This security level is primarily designed for InfoPath forms that are deployed using email.     
> - If you select the **Full Trust** security level, you need to digitally sign or install and register the form. For more information, see [Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md).
    
The following table summarizes the InfoPath security model. The first column lists the level specified for or required by the form. The second and third columns specify whether the form has a URN or URL identifier for its location. The remaining columns specify what is allowed to run. For more information on deployment scenarios and permission sets for managed code form templates, see the "Common Language Runtime Code Access Security Features" section later in this topic.
  
|**Level Required by form**|**Has URN Identifier**|**Has URL Identifier**|**ActiveX marked unsafe for scripting**|**Cross-Domain Access**|**Managed code**|**Object Model Security**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Restricted  <br/> ||X  <br/> |No ActiveX at all  <br/> |Fail  <br/> |Form loads, but managed code won't run  <br/> |0  <br/> |
|Domain (Internet Explorer **Restricted sites** zone)  <br/> |Won't run at all  <br/> |Won't run at all  <br/> |Won't run at all  <br/> |Won't run at all  <br/> |Won't run at all  <br/> |Won't run at all  <br/> |
|Domain (Internet Explorer **Internet** zone)  <br/> |X  <br/> ||Fail  <br/> |Fail  <br/> |Won't run at all  <br/> |0  <br/> |
|Domain (Internet Explorer **Local intranet** zone)  <br/> |X  <br/> ||Fail  <br/> |Prompt  <br/> |Managed code runs with **Local intranet** permissions. |2  <br/> |
|Domain (Internet Explorer **Trusted sites** zone)  <br/> |X  <br/> ||Prompt  <br/> |OK  <br/> |Managed code runs with **Internet** permissions. Cross-domain access is allowed. Note that even though the form is in the **Trusted sites** zone, **Internet** zone permissions are applied. |2  <br/> |
|Domain (Internet Explorer **Local computer** zone)  <br/> |X  <br/> |X  <br/> |Prompt  <br/> |Fail  <br/> |Managed code runs with **Local intranet** permissions. |2  <br/> |
|Full Trust  <br/> |X  <br/> |X  <br/> |OK  <br/> |OK  <br/> |Full Trust  <br/> |3  <br/> |
   
> [!IMPORTANT]
> The descriptions above in the "ActiveX marked unsafe for scripting" and "Cross-Domain Access" columns assume the default security settings for Microsoft Internet Explorer. If a user changes their security settings, InfoPath will behave accordingly. For example, if in the **Local intranet** zone, **Access data sources across domains** is set to **Enable**, then users will not be prompted to allow cross-domain access as described in the table. 
  
## Common Language Runtime Code Access Security Features

When an InfoPath managed code form template is compiled, a private managed code assembly is created that contains the implementation of the form code logic.
  
In the .NET Framework, by default, a managed code assembly has Full Trust permissions when running on the local machine, and is not granted Full Trust permissions when running on the Intranet. To provide more fine-grained control over security policy, and to provide the option to run InfoPath managed code form templates as fully trusted forms from the Intranet, InfoPath implements the following security architecture.
  
- The InfoPath application hosts the .NET Framework common language runtime (CLR).
    
- Within the CLR hosted by InfoPath, each managed code form template runs in a separate application domain, which is an environment that provides isolation, unloading, and security boundaries for executing managed code.
    
- InfoPath sets a default security policy on the application domain depending on the level of trust associated with the form template and the URL of its location.
    
- By default, a managed code form template running on the local computer (the My Computer Zone code group) gets a lower level of permissions than Full Trust (Local Intranet Zone permissions). To have Full Trust permissions, the form must be registered or digitally signed with a trusted certificate.
    
The default security policy set for the application domain of a managed code form template ensures that the InfoPath domain access security levels as well as any additional .NET security restrictions are enforced. To provide additional flexibility, the InfoPath security system recognizes a .NET code access security code group named "InfoPath Form Templates". If this code group is present on a user's computer, its security configuration, and those of any child code groups within it will be applied to the application domain.
  
> [!IMPORTANT] 
> - The InfoPath Form Templates code group applies only to the managed code form code assembly itself. As a result, if you grant the Full Trust permission set to InfoPath managed code form code, but you have not installed and registered (or digitally signed) the form template itself (which makes the entire form template fully trusted), calls in the form code to security level 3 object model members will still fail.   
> - If you reference or explicitly load (Assembly.Load) an assembly that is configured with a restricted permission set using Hash, Strong Name, or Publisher evidence to determine its membership condition in a form template project, the assembly will nonetheless be loaded and executed by the form template.
    
For information on how to create and configure the InfoPath Form Templates code group, see [Configure Security Settings for Form Templates with Code](how-to-configure-security-settings-for-form-templates-with-code.md).
  
The following table summarizes the deployment scenarios and permission sets that apply to managed code form templates.
  
|**Deployment Scenario**|**Permission Set**|**Notes**|
|:-----|:-----|:-----|
|The form template is published on the local computer, and the developer is using Visual Studio to write and debug form code. |Local Intranet permission set. Assemblies installed in the Global Assembly Cache (GAC) and marked with the **AllowPartiallyTrustedCallersAttribute** attribute are granted the Full Trust permission set. |By default, form templates running from the local computer are not granted the Full Trust permission set. While developing form templates that use features and calls to object model members that require Full Trust permissions, you can use the procedure described in [Preview and Debug Form Templates that Require Full Trust](how-to-preview-and-debug-form-templates-that-require-full-trust.md). |
|The form template is published on the local computer and references a custom assembly that requests the Full Trust permission set on the local computer. |Local Intranet permission set. Assemblies installed in the Global Assembly Cache (GAC) and marked with the **AllowPartiallyTrustedCallersAttribute** attribute are granted the Full Trust permission set. The custom assembly is granted the Local Intranet permission set. |To reference external assemblies for use in the form template's code, the developer must use the InfoPath Form Templates code group to grant Full Trust (or the appropriate permission set) to the external assembly referenced in the form template's code. InfoPath does not make any assumptions about external assemblies other than those installed in the Global Assembly Cache (GAC). The developer must explicitly grant the assembly the necessary permissions using the InfoPath Form Templates code group even if the assembly is already trusted though permissions granted in the My_Computer_Zone code group. |
|The form template is published on a shared location in the local intranet, such as a file share, SharePoint Form library, or a Web server. |Local Intranet permission set. Assemblies installed in the Global Assembly Cache (GAC) and marked with the **AllowPartiallyTrustedCallersAttribute** attribute are granted the Full Trust permission set. ||
|The form template is published on a shared location in the local intranet, such as a file share, SharePoint Form library, or a Web server that is designated as a Trusted site in Internet Explorer. |Internet permission set. Assemblies signed by Microsoft and ECMA are granted the Full Trust permission set. |CLR code access security grants only the Internet permission set to sites that are designated as Trusted sites in Internet Explorer. InfoPath respects this policy. Note that this is unlike an InfoPath form template that uses script for form code, which receives a higher level of permissions when published in a Trusted sites zone. |
|The form template is downloaded or copied from an Internet location. |By default, none. The managed code assembly for the form template is not loaded and does not run. ||
   
## See also

- [Configure Security Settings for Form Templates with Code](how-to-configure-security-settings-for-form-templates-with-code.md)
- [Preview and Debug Form Templates that Require Full Trust](how-to-preview-and-debug-form-templates-that-require-full-trust.md)

