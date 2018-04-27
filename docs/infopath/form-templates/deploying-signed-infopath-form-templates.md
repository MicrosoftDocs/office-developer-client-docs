---
title: "Deploying Signed InfoPath Form Templates"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 8345a4bc-ad7b-d0b0-7615-f77ade35006d
description: "Before reading this topic, see theSigned Form Templatessection in Additional InfoPath Form Security Concepts for an understanding of signed form template security. Information and discussions in the Security Levels, E-Mail Deployment, and Remote Form Templates topic are also relevant."
---

# Deploying Signed InfoPath Form Templates

Before reading this topic, see the "Signed Form Templates" section in [Additional InfoPath Form Security Concepts](additional-infopath-form-security-concepts.md) for an understanding of signed form template security. Information and discussions in the [Security Levels, E-Mail Deployment, and Remote Form Templates](security-levels-e-mail-deployment-and-remote-form-templates.md) topic are also relevant. 
  
## Digitally Signing a Form Template

If you digitally sign a form template, you can set the security level for the form template to Full Trust, which means the form can access files and settings on the user's computer or on a different domain. (Also, digitally signing a form template does not prevent you from using other security levels, if you prefer. You set the security level of a signed form template to the Domain or Restricted security level.) In addition, you can deploy the signed form template to users who are using an e-mail program and then later automatically update the signed form template by sending the updated version to the users as an attachment to an e-mail message, follow these steps:
  
### To digitally sign a form template

1. In the InfoPath designer, click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
2. In the **Form Options** dialog box, click the **Security and Trust** category. 
    
3. Under **Form Template Signature**, select the **Sign this form template** check box. 
    
4. Click **Select Certificate**.
    
5. In the **Select Certificate** dialog box, click the certificate that you want to use to digitally sign the form. 
    
> [!NOTE]
> The **Create Certificate** button in the **Form Options** dialog box can be used to generate a test certificate to sign a form template. The test certificate should be used to sign form templates for testing only. Test certificates should not be used to sign form templates that will be distributed publicly. Because the certificates are not issued by a Certificate Authority whose root certificate is already trusted on a user's computer, the test certificate will not validate correctly on the user's computer. If you deploy a form template signed with a test certificate, users of your form template will most likely be unable to open it. 
  
## Establishing a Trusted Root Certificate and Publisher

 The trusted root certificate of the certificate that is used to sign the form template must be in the trusted root certificate store on the client computer. If not, the publisher of the form template cannot be verified, and users of your form template will not be given the option to trust the publisher. If the trusted root certificate is in the trusted root certificate store, but the publisher is not in the trusted publisher list, users are prompted and given the option to trust the publisher of the form template. 
  
> [!NOTE]
> If a signed form template requests Domain or Restricted access, InfoPath will use the signature to verify that the form template was not tampered with after it was signed. InfoPath also uses the signature to determine whether the form template can be updated automatically. 
  
## Deploying Signed Form Templates with Full Trust Access

The primary scenario for deploying signed form templates is to enable domain-like functionality, such as automatic update, in full-trust forms. A signed form template requesting full-trust access has the same access to system resources as a  *fully trusted form*  . For a detailed discussion of how fully trusted forms work and how to create and deploy them, see [Understanding Fully Trusted Forms](understanding-fully-trusted-forms.md).
  
However, depending on your organization's computing environment, you might prefer to use either signed form templates or fully trusted forms. For example, there are benefits to using a signed form template that requests full-trust access instead of a registered, fully trusted form. A signed form template requesting full-trust access has the following benefits:
  
- Does not have to be registered, unlike an unsigned, fully trusted form template.
    
- Enables silent automatic update of the form template.
    
Because you do not have to register a signed form template that requests full-trust access, you do not have to use an installer package or script file to deploy it. This benefit greatly simplifies the deployment of a full-trust form template.
  
When you update your signed form template that requests full-trust access, you can just send the updated template to the user or update it in a shared location. When the user opens the updated template, the user will not be prompted, and the updated version will silently overwrite the older copy on the user's computer. If you updated the template in a shared location, the user will be able to use the updated copy without being prompted.
  
If you want to update an unsigned, fully trusted form, you must repackage your form and re-register it. Additionally, an existing, installed fully trusted form template works only for the path of the local computer but does not work for a network path, because the registration process does not support changing a local computer path to a network path. However, because a certificate is needed to sign a form template, you may prefer to deploy fully trusted, registered form templates, if you do not want to purchase a certificate.
  
## Deploying Signed Form Templates with Domain or Restricted Access

A signed form template that has a Domain or Restricted security level also has the advantage of the automatic update functionality. For example, you could publish a signed form template to a document library on a server that is running Microsoft SharePoint Foundation or on a server that has a Domain security level. When you update your form template in the shared location, users will get the updated copy automatically.
  

