---
title: "Security Guidelines for Developing InfoPath Forms"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
 
 
ms.localizationpriority: medium
ms.assetid: 4690028e-20ac-297b-4651-801f5159c747
description: "Before reading this topic, see Additional InfoPath Form Security Concepts for a general understanding of the InfoPath security model."
---

# Security Guidelines for Developing InfoPath Forms

Before reading this topic, see [Additional InfoPath Form Security Concepts](additional-infopath-form-security-concepts.md) for a general understanding of the InfoPath security model. 
  
## Security Issues for Users of InfoPath Forms

The primary security concerns for users of Microsoft InfoPath are similar to those for Web applications running in Internet Explorer. You should note, however, that the security level provided to a form depends only on where the form template is located and not on where users store or open the resulting XML documents they create. Users can determine the location of the form template they are working with by looking at the status bar in InfoPath.
  
InfoPath helps protect users against the following potential threats posed by maliciously authored form templates:
  
- The potential for disclosure of sensitive information from the local computer or remote data sources.
    
- The malicious use of ActiveX controls.
    
- The malicious use of properties and methods from the InfoPath object model.
    
## Disclosure of Sensitive Information

The most common scenario for the disclosure of sensitive information can occur if a malicious form author creates a form that uses the current user's security credentials to access a data source on a domain other than the one on which the form itself was deployed. For example, a malicious user could send a form by email message or by using a URL to a form on a private share or Web server. The form could contain script that performs a data access request by using the current user's credentials to retrieve data from a data source in another domain that the malicious user would not otherwise have access to, such as a database of payroll or other sensitive information. This class of security risk scenarios is referred to as cross-domain data access.
  
The Internet Explorer security model that InfoPath is built upon provides a setting called **Access data sources across domains** that, by default, disables cross-domain access for InfoPath forms that reside in the **Internet** and **Restricted sites** security zones. This setting also prompts the user to allow or disallow cross-domain access for InfoPath forms that reside in the **Local intranet** security zone, and it enables cross-domain access for InfoPath forms that reside in the **Trusted sites** or **Local Machine** zones. 
  
## Malicious Use of ActiveX Controls

The primary scenario for the malicious use of ActiveX controls is when a malicious form author writes code against an ActiveX control that accesses the file system to retrieve personal files and password lists, delete files, or disable the user's system. An InfoPath form can run code against ActiveX controls only from business logic or from script running in a task pane. InfoPath does not allow scripts in InfoPath views to run ActiveX controls.
  
The Internet Explorer security model that InfoPath is built upon provides a setting called **Initialize and script ActiveX controls marked as unsafe**. This setting, by default, disables initializing and scripting ActiveX controls marked as unsafe for InfoPath forms that reside in the **Local intranet**, **Internet**, and **Restricted sites** security zones. It prompts the user to allow or disallow scripting of ActiveX controls marked as unsafe for InfoPath forms that reside in the **Trusted sites** or the **Local Machine** security zones, and it enables scripting of ActiveX controls marked as unsafe for InfoPath forms that are fully trusted. 
  
In addition, you cannot insert an ActiveX control that is marked as unsafe for initializing and scripting into the controls task pane while in design mode, regardless of which security zone you are in or the trust level of the form.
  
## Malicious Use of InfoPath Object Model Code

Similarly, InfoPath methods and properties called from code can present different levels of risk. For example, the [SaveAs(String)](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.SaveAs.aspx) method of the [XmlForm](https://msdn.microsoft.com/library/Microsoft.Office.InfoPath.XmlForm.aspx) class can be used to write data anywhere in the file system. To help protect against malicious use of these object model members, the InfoPath object model implements three levels of security that determine how and where a particular object model member can be used. For more information on this feature, see [About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md).
  
## Best Practices for Developers of InfoPath Forms

Developers creating InfoPath forms should know how to implement the following security best practices:
  
- How to recognize potential security issues in the XML file associated with a form.
    
- How to avoid presenting confusing or annoying error messages to form users.
    
- How to sign the CAB files of ActiveX controls.
    
- How to sign form templates sent as an attachment to an email message.
    
## Best Practices for XML Data Associated with a Form

Note that InfoPath forms can be fed XML data from any source, including those that the user does not necessarily trust or control. For example, InfoPath can get XML data from a link to a Web page or from an XML attachment sent to the user in email message. To mitigate these risks, be aware of the following best practices:
  
- Do not pass untrusted data that is read from the XML to the Microsoft JScript **eval()** function or the **innerHTML** property of the task pane. Both of these calls could be used to execute malicious script. In a task pane, use the **innerText** property as an alternative. Note that InfoPath views cannot execute script. 
    
- Data submitted to a database from an XML file can present security risks to the database if it is not validated before submission.
    
Data that is not validated before submitting it to a data source can damage the integrity of the data in the data source, or in more extreme cases, present the potential for buffer overruns. It is also possible to cause script injection or SQL injection if you try to use untrusted data directly on your server.
  
## Best Practices to Avoid Presenting Confusing Error Messages

 **Deploy forms and their data sources on the same domain**
  
The security risk of cross-domain data access is not clearly understood by most users. Deploying forms that continually warn and prompt users about allowing cross-domain data access has the effect of training many users to approve all cross-domain access requests, or to add the originating domain to their **Trusted sites** list, without taking the security risks seriously. To avoid this situation, deploy InfoPath forms on the same server as any data sources on which they depend. 
  
 **Avoid using ActiveX controls that are not marked as safe for scripting**
  
ActiveX controls can potentially expose properties and methods that can be used to compromise a user's system, such as methods for accessing the file system of a computer. Whenever possible, you should use only ActiveX controls that are marked safe for scripting. These are controls that have been tested to ensure they will not damage a user's system or compromise the user's security, regardless of how the control's methods and properties are manipulated by a Web page's script. Similarly, when creating ActiveX controls for use with InfoPath, inspect the code and test the ActiveX control rigorously before marking it safe for scripting.
  
InfoPath uses a security model that is based on Internet Explorer's security zones. Therefore, an InfoPath form will use the same permissions as Internet Explorer, which by default enables script calls to ActiveX controls marked safe for scripting, without prompting users.
  
## Best Practices for Managing the CAB Files of ActiveX Controls

ActiveX controls can be hosted in form templates designed for the InfoPath editor. CAB files for these controls that are not already present on the user's computer must be included in the form template (.xsn) file. CAB files included in form templates must be digitally signed in order for the CAB file to be installed. InfoPath will not install a CAB file that is not signed, regardless of trust level or security zone.
  
To ensure that the digital signature on the CAB file can be verified, the file should be signed with a certificate that has a trust chain leading to an already trusted certificate root. Otherwise, the signature cannot be authenticated, the signature verification will fail, and the CAB file will not be installed.
  
## Best Practices for Form Templates Sent as an Attachment to an Email Message

InfoPath supports deploying form templates as an attachment to an email message and moving form templates from one location to another. It is good security practice to digitally sign a form template that you design and intend to deploy as an attachment to an email message. A digital signature on a form template deployed by email message not only ensures the authenticity of the template. It also has the added benefit of allowing the form template to be updated automatically.
  
The form template should be signed with a certificate that has a trust chain leading to an already trusted certificate root. If it is not signed with such a certificate, signature verification will fail, because the signature cannot be authenticated.
  
> [!NOTE]
> If a signed form template requests Domain or Restricted access, InfoPath will not check or verify the signature except to determine whether InfoPath can automatically update the template. 
  
You can find more information about email deployment in [Security Levels, E-Mail Deployment, and Remote Form Templates](security-levels-email-deployment-and-remote-form-templates.md).
  

