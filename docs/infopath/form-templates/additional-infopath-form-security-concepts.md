---
title: "Additional InfoPath Form Security Concepts"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 77425a61-bf33-b3d8-442a-caee48e54a48
description: "The Microsoft InfoPath security model is based on the security model implemented by Internet Explorer. The Internet Explorer security model helps protect your computer from unsafe operations by using security zones and levels. Working together with the Internet Explorer security model, InfoPath provides for two kinds of form deployment that affect how an InfoPath form works within this security model."
---

# Additional InfoPath Form Security Concepts

The Microsoft InfoPath security model is based on the security model implemented by Internet Explorer. The Internet Explorer security model helps protect your computer from unsafe operations by using security zones and levels. Working together with the Internet Explorer security model, InfoPath provides for two kinds of form deployment that affect how an InfoPath form works within this security model.
  
- **URL-based Forms** This deployment method is the default when publishing a form from InfoPath to a Web server, SharePoint Foundation form library, or file share. These forms are known as URL-based forms because a user typically opens the form from the URL where the form is published, and that URL is specified in the **publishUrl** attribute of the **xDocumentClass** element in the form definition file (.xsf). URL-based forms are said to be sandboxed, because they have restricted access to system resources and other potential areas of risk. A URL-based form has the same level of permissions as a Web page that is opened from the same location as the form template file (.xsn).
    
- **URN-based Forms** This deployment method is for forms that require access to system resources and other external resources, such as ActiveX controls and other software components. You can deploy InfoPath forms as fully trusted forms. Such forms are also known as URN-based forms because, instead of specifying the **publishUrl** attribute, they specify a Uniform Resource Name (URN) in the **name** attribute of the **xDocumentClass** element in the form definition file (.xsf). This class of form can request full trust if the **requireFullTrust** attribute of the **xDocumentClass** element is set to  `"yes"` in the form definition file (.xsf). URN-based forms must be registered on the client computer by an installation program or script. In this case, the form gets the same permissions as an application that is running on the local computer. 
    
In conjunction with these two methods of form deployment, every method and property in the InfoPath object model has a security level that controls when that method or property can be called from script running from the form.
  
## Understanding InfoPath Integration with the Internet Explorer Security Model

Internet Explorer implements security zones that let you control the level of access given to your computer by the Web pages that you open. InfoPath uses some of these zones to determine the level of access that forms are given to the resources on your computer. By default, InfoPath forms run in a cached location that is denied access to critical system resources. Forms that are allowed full access to system resources are called fully trusted forms. Fully trusted forms are usually installed and registered by using an installation program or script, or they are digitally signed so that they can be granted a higher level of permissions.
  
InfoPath cached forms are identified by the URL or URN specified in the form's form definition file (.xsf). The kind of identification used and the domain (location) from which the form template is opened determines which Internet Explorer security zone permissions the form will inherit. Forms identified by a URL are cached to the user's computer, which enables offline use of the form. These URL-based forms inherit their security permissions and their specific access rights, such as cross-domain access, from the Internet Explorer security settings applicable to the original location of the form template. Form templates stored on a Web server or a server running SharePoint Foundation run in the Internet or the Local intranet zone, depending on the server's domain. Installed forms that are identified by a URN, on the other hand, inherit their permissions from the Local Computer zone, which grants a level of permissions similar to that for HTML application files (.hta).
  
Fully trusted forms are identified by their URN and whether the **requireFullTrust** attribute of the **xDocumentClass** element in the form definition (.xsf) file is set to  `"yes"`. In InfoPath, after fully trusted forms are installed, they appear on the **New** tab in the Microsoft Office Backstage of InfoPath editor. 
  
For a detailed discussion of how fully trusted forms work and how to create and deploy them, see [Understanding Fully Trusted Forms](understanding-fully-trusted-forms.md).
  
## Trusting Installed Forms

The ability to use trusted forms can be enabled or disabled on individual computers. When a computer is configured to trust installed forms, users can fill out forms that require access to their computer's resources.
  
In the InfoPath editor, you configure a computer to trust installed forms in the Backstage by clicking **Options**, **Trust Center**, **Trust Center Settings**, and then selecting the **Allow fully trusted forms to run on my computer** check box on the **Trusted Publishers** tab of the **Trust Center** dialog box. 
  
## Using Security Features in InfoPath

The InfoPath security model helps protect users against the following threats posed by maliciously authored templates:
  
- The potential for disclosure of sensitive information from your local computer or remote data sources.
    
- The malicious use of ActiveX controls.
    
- The malicious use of properties and methods from the InfoPath object model.
    
## Cross-domain Data Access

Of security risk scenarios is referred as cross-domain data access.
  
The Internet Explorer security model that InfoPath is built upon provides a setting called **Access data sources across domains**. By default, this setting disables cross-domain access for InfoPath forms that reside in the Internet and Restricted sites security zones. It prompts the user to allow or disallow cross-domain access for InfoPath forms that reside in the Local intranet security zone, and it enables cross-domain access for InfoPath forms that reside in the **Trusted sites** or **Local Machine** zones. 
  
## Use of the InfoPath HTML Task Pane

The InfoPath HTML task pane enables rendering of Web pages, such as .htm, .asp, and .hta files. The pages referenced from task panes can be located inside or outside the form template. The only restriction on what can be referenced from outside the form template is that the Web page must be in the same domain as the form template, or the security zone in which the template resides must allow cross-domain access permissions to load the task pane.
  
The task pane does not expose an address bar or status bar, and therefore, the user has no way of confirming the location of the source for the task pane or whether that location is being accessed over a encrypted channel (https). For this reason, you should avoid using the task pane for displaying or entering sensitive information. The task pane was designed for displaying dynamic help information and controls for navigating between views and other elements of an integrated solution. Additionally, a form template's business logic and script in the task pane can interact with one another. However, this interaction is allowed only if the form template and the task pane are in the same domain, which helps prevent information from being exchanged across domains.
  
## Cross-domain Data Access Prompts

If a form template that requires cross-domain data access is located in a security zone that is set to prompt for cross-domain data access (the default setting for the Local intranet zone), then the user will be prompted whether to allow access. The user's choice will then persist for the rest of the time that the form is opened. If you must deploy InfoPath form templates that require cross-domain data access, you should deploy these templates as fully trusted forms, or make them available on a server that is in the Trusted sites security zone, to avoid prompting users to allow access. Users should not be instructed to lower the security level of the Local intranet zone to avoid these prompts.
  
## Forms Without a publishURL Attribute

If InfoPath loads a form template from the local computer and it has a blank **publishUrl** attribute or the attribute is missing, the form will be placed in a more restrictive security zone. This is performed to reduce the threat of a malicious form template being distributed by email. As a result, if the user saves this form template to disk, it will be unable to run with the permissions of a form that resides in the **Local Machine** zone. 
  
## Unsafe ActiveX Controls

The most common scenario for the malicious use of ActiveX controls can occur if an author uses script with an ActiveX control that provides methods for accessing the file system to retrieve personal files and password lists, to delete files, or to disable the user's system. An InfoPath form can use ActiveX controls only from script in the main scripting file of a form (script.js) or from script in a task pane. InfoPath does not allow script in InfoPath views to run ActiveX controls.
  
The Internet Explorer security model that Microsoft InfoPath is built upon provides a setting called **Initialize and script ActiveX controls marked as unsafe** that, by default, results in the following actions for InfoPath forms or task panes that attempt to initialize and script ActiveX controls that are marked as unsafe for scripting. 
  
|**Security Zone/Deployment**|**Action**|
|:-----|:-----|
|Internet  <br/> |Disabled  <br/> |
|Local intranet  <br/> |Disabled  <br/> |
|Restricted sites  <br/> |Disabled  <br/> |
|Trusted sites  <br/> |Prompt  <br/> |
|My Computer  <br/> |Prompt  <br/> |
|Fully trusted form  <br/> |Enable  <br/> |
   
## Malicious Use of the InfoPath Object Model

Similarly to ActiveX controls called from script, InfoPath methods and properties called from code can present different levels of risk. For example, the [SaveAs(String)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SaveAs.aspx) method of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class can be used to write data anywhere in the file system. 
  
To help protect against malicious use of InfoPath object model members, the InfoPath object model implements three levels of security that determine how and where a particular object model member can be used. There are three security levels in the InfoPath object model:
  
- **0** Object model members that can be accessed without restrictions. These object model members are safe and therefore can be accessed without restrictions. 
    
- **2** Object model members that can be accessed only by forms running in the same domain as the currently open form, or by forms that have been granted cross-domain data access permissions. Restricted form templates that call security level 2 object model methods will only succeed if they are accessing resources contained in the form template itself. 
    
- **3** Object model members that can be accessed only by fully trusted forms. 
    
- Each of the topics for the properties and methods in the InfoPath Object Model Reference contains a security section that specifies the security level that applies to that object model member.
    
- Security level **1** is reserved for future use. 
    
## Summary

The following table summarizes the default permissions for each method of form deployment in InfoPath. Permissions are based on the security zone for the domain from which the form template originates.
  
|**Security Zone**|**Deployment**|**Default Permissions**|
|:-----|:-----|:-----|
||**URL-based** <br/> |**URN-based** <br/> |**ActiveX Marked Unsafe for Scripting** <br/> |**Cross-domain Data Access** <br/> |**Object Model Security Level** <br/> |
|Restricted sites  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |N/A  <br/> |
|Internet  <br/> |X  <br/> ||Disable  <br/> |Disable  <br/> |2  <br/> |
|Local intranet  <br/> |X  <br/> ||Disable  <br/> |Prompt  <br/> |2  <br/> |
|Trusted sites  <br/> |X  <br/> ||Prompt  <br/> |Enable  <br/> |2  <br/> |
|Local Machine  <br/> |X  <br/> |X  <br/> |Disable  <br/> |Prompt  <br/> |2  <br/> |
|Fully trusted form  <br/> |X (signed by a Trusted Publisher)  <br/> |X  <br/> |Enable  <br/> |Enable  <br/> |3  <br/> |
|Fully trusted form  <br/> ||X  <br/> |Enable  <br/> |Enable  <br/> |3  <br/> |
|Restricted  <br/> ||X  <br/> |No ActiveX (except a limited hard-coded list)  <br/> |Disable  <br/> |2  <br/> |
|Restricted  <br/> |X  <br/> ||No ActiveX (except a limited hard-coded list)  <br/> |Disable  <br/> |2  <br/> |
|Restricted  <br/> |X  <br/> |X  <br/> |No ActiveX (except a limited hard-coded list)z  <br/> |Disable  <br/> |2  <br/> |
   
For information about general security guidelines when you develop forms, see [Security Guidelines for Developing InfoPath Forms](security-guidelines-for-developing-infopath-forms.md).
  
## Understanding Other Security Features

InfoPath provides other security measures for forms that include protecting form design by using digital signatures, managing certain form operations such as merging and submission, and trusting installed forms. The following sections describe these form security measures and where they are enabled in InfoPath.
  
## Digital Signatures

The data that is contained in a form can be digitally signed to help ensure that its contents are not altered.
  
You configure a form to use digital signatures by selecting the **Allow signing the entire form** or **Allow signing parts of the form** option on the **Digital Signatures** section of the **Form Options** dialog box, which is available from the Microsoft Office Backstage in the InfoPath form designer. When filling out the form, users can then sign and verify forms by clicking the **Sign Form** button on the **Info** tab of the Microsoft Office Backstage. When the form is opened again, the user will be alerted if the contents of the form have been altered. 
  
-  Digital signatures can be enabled for the entire form or for specific sets of data in the form that can be signed separately. 
    
- You can choose to sign only specific sections of a form instead of the whole form.
    
- You can specify whether to allow single or multiple signatures. You can also specify what the relationship is for each set of data that can be signed. For example, you can specify whether the signatures are parallel co-signatures or whether each new signature countersigns all the earlier ones.
    
- You can use the InfoPath object model to programmatically add custom information to the signature block in a fully trusted form.
    
- You can improve the security of digital signatures by capturing and including additional information, such as a time stamp, as non-repudiation evidence. Because the additional evidence is part of the signature, it cannot be removed without invalidating the signature. You can at any time recall or examine the captured data by clicking a digital signature in the form, or by selecting a digital signature from the list of digital signatures displayed in the **Digital Signatures** dialog box. 
    
-  You can insert and see a signature in the document, and view the form as it was presented to each signer. 
    
- The digital signature also includes a snapshot of the view as it was presented to the signer when the form was signed. The snapshot is stored as a base64-encoded image in the standard PNG file format. 
    
## Email Deployment

You can deploy your form templates as an attachment to an email message and move the form templates from one location to another. Mail deployment is an easy and effective way to distribute forms for interoffice use and to deploy forms to remote users.
  
You can digitally sign a form template that you design and then set the security level for that form template to Full Trust. Additionally, signed fully trusted forms, when they are deployed as an email attachment, can be updated more easily and efficiently.
  
All forms in the InfoPath designer are created with an identity. This information helps InfoPath associate forms with form templates in the cache and retrieve updates to forms when they are posted to a shared location. By default, InfoPath creates two identities for form templates: a Form ID and an Access Path (also known as the **publishURL** attribute). You can find more information about email deployment in the [Security Levels, E-Mail Deployment, and Remote Form Templates](security-levels-email-deployment-and-remote-form-templates.md)topic.
  
## ActiveX Controls

InfoPath supports hosting ActiveX controls in forms that are opened in the InfoPath editor. The ActiveX controls can be preexisting (with some constraints) or can be written specifically for use with InfoPath. ActiveX controls that are used in InfoPath forms are not downloaded automatically from Web sites. Instead, CAB files for the ActiveX controls that are not already present on the user's computer must be added to the form template file.
  
When an ActiveX control is used in a form and the control is not registered on the user's computer, the behavior when the form is opened depends on the ActiveX control settings within the form. If no CAB file is included in the form template file, InfoPath will not open the form. If the CAB file is present in the form template file, InfoPath will start an installation process. For InfoPath to install a CAB file, the file must be signed, and the signature must be from a trusted publisher. If the publisher is not already in the user's trusted publisher list that has a certificate present (with a trust chain leading to a trusted certificate root), the user will be prompted to either accept or decline trusting the publisher. If the user chooses not to trust the publisher, the CAB file for the control will not be installed, and InfoPath will not open the form.
  
> [!NOTE]
> ActiveX controls must be marked as "Safe for scripting" and "Safe for initialization with untrusted data" in order to be used in InfoPath. 
  
## .NET Security

In addition to InfoPath-specific security levels, managed-code form templates also support additional code access security features that apply to managed code running under the Common Language Runtime (CLR) of the Microsoft .NET Framework.
  
If your form is fully trusted, it can automatically access resources outside the form template. Any assembly can be used in the business logic code. You can customize the permission set that is added to a managed-code form template using the Microsoft .NET Framework Configuration Tool or the Code Access Security Policy tool (Caspol.exe). InfoPath will look for a predefined code group and will apply the permissions set that is defined under that group to the application domain (AppDomain) where the managed code is loaded and from which it runs. Custom .NET security policies must be deployed to client computers where the managed-code form template will run.
  
Note that .NET security grants the Internet permission set only to managed code running in Internet Explorer Trusted Sites. Therefore, InfoPath managed-code forms will not run if they are published to a Trusted Site.
  
## Merging Forms

You can disable the form merging feature to prevent users from importing data from multiple forms into a single form.
  
You enable or disable form merging by using the **Enable form merging** check box on the **Advanced** section of the **Form Options** dialog box, which is available from the **Info** tab of the Microsoft Office Backstage when you design the form. When form merging is disabled, users cannot click **Merge Forms** on the **Share** tab of the Microsoft Office Backstage when filling out a form. 
  
## Submitting Forms

You can disable the form submission feature to prevent users from submitting forms.
  
You enable or disable form submission by using the **Submit Options** dialog box, which is available by clicking **Submit Options** on the **Data** tab menu in design mode. When form submission is disabled, users cannot click **Submit** on the **Home** tab when filling out a form. 
  

