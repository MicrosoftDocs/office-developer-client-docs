---
title: "Security Levels, E-Mail Deployment, and Remote Form Templates"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 7fc438ad-ae26-3632-3444-371537eaecb3
description: "Microsoft InfoPath supports moving form templates from one location to another, sending them as an attachment to an e-mail message, and creating Full Trust form templates that are digitally signed or installed."
---

# Security Levels, E-Mail Deployment, and Remote Form Templates

Microsoft InfoPath supports moving form templates from one location to another, sending them as an attachment to an e-mail message, and creating Full Trust form templates that are digitally signed or installed.
  
## Security Levels

Form templates can have one of three security levels, depending on where the form is located. These three security levels are described in the following sections. 
  
## Restricted

The Restricted security level does not allow any communication outside the form template. This security level is intended to prevent harmful forms from transmitting any data from your computer to a malicious attacker. When running in this security mode, the following features will not work:
  
- HTML Task Panes
    
- SharePoint Query
    
- SharePoint Submit
    
- XML File Query
    
- Database Query
    
- Database Submit
    
- Web Service Query
    
- Web Service Submit
    
- Custom Code Submit
    
- Hosting Environment Submit
    
- ActiveX Controls
    
- Roles
    
- SharePoint Workflow
    
- Rules that open a New Document
    
- Managed Code
    
- External Print View
    
- Linked Images
    
- Linked Images
    
## Domain

The Domain security level restricts a form to a particular Internet domain and its permissions are restricted to the Internet Explorer settings for the zone where the domain is located. The form is allowed to communicate with other data sources inside its own domain but is typically not allowed to retrieve data from other domains unless the zone allows cross-domain communication. This is the minimum security level allowed for browser-compatible form templates.
  
## Full Trust

The Full Trust security level allows you to run a form with full trust on the computer where the form will be used. This security level can only be used when you are working with a form located on a server that is signed with a signature that matches a trusted root publisher on your computer, or by installing the form. Both methods require setting the **requireFullTrust** attribute to "yes". By using this setting, the form can access object model calls such as file save, and certain security prompts that appear when you run at a more restrictive security level are disabled. 
  
> [!NOTE]
> All forms generated in the InfoPath designer have a security level associated with them. InfoPath opens forms at their associated security level. If the security level associated with the form is higher than the security level that can be granted to it, the form will not open. 
  
The Full Trust security level can only be set for installed or signed form templates; otherwise, the maximum trust level is Domain. InfoPath will not set a security level to Full Trust automatically.
  
Forms are granted security levels based on the location from which the form is opened.
  
## Trust Levels

The highest level of trust that can be granted to a form template is determined by the Opened From location and other verification code, as described in the following table. The attributes listed in the table (for example, HTTP, UNC,  *requireFullTrust*  ) are entries that are used to determine the level of trust that can be granted to a form, and apply to forms opened in the InfoPath client. 
  
|**Highest Level of Trust Granted**|**Full Trust**|**Client Computer (Sandboxed)**|**Intranet (Sandboxed)**|**Internet (Sandboxed)**|**Restricted**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|**file: Access Path=Opened From Location** <br/> |||X  <br/> |||
|**file: Access Path\<\>Opened From Location or no Access Path (regardless of where the form came from)** <br/> |||||X  <br/> |
|**Opened From Location: Intranet HTTP or HTTPS** <br/> |||X  <br/> |||
|**Opened From Location: Internet HTTP or HTTPS** <br/> ||||X  <br/> ||
|**Opened From Location: UNC** <br/> |||X  <br/> |||
|**Installed Template (requireFullTrust="yes")** <br/> |X  <br/> |||||
|**Installed Template (requireFullTrust="no")** <br/> ||X  <br/> ||||
|**Template with trusted publisher certificate** <br/> |X  <br/> |||||
|**Exported Form Files** <br/> |||X  <br/> |||
   
## Form Open Behavior

All form files opened in the InfoPath editor are bound by a set of conditions that determine the security level at which the form will open and whether it will open. When an InfoPath form is opened in the editor, it will be either opened with an appropriate security level, or it will not load. If a form requests a higher security level than it can be granted (a form can request a specific security level using the **trustLevel** or **requireFullTrust** attribute), it will not be allowed to load. Otherwise, it will be loaded with the security level it requests. If the form template is not allowed to open with the requested security level, the user will not be able to open the form and will receive an error message. 
  
The following table describes the conditions required for opening a form at each security level and the resultant behavior when the user attempts to open the form.
  
|**Editor Opens/Fails**|**Full Trust (requireFullTrust="yes")**|**Domain Trust (trustLevel="Domain" or blank)**|**Restricted (trustLevel="Restricted")**|
|:-----|:-----|:-----|:-----|
|**Trusted (installed or trusted certificate)** <br/> |Editor opens at Full Trust level  <br/> |N/A  <br/> |N/A  <br/> |
|**Domain Trust: Client Computer** <br/> |Fails to open  <br/> |Editor opens at Domain level  <br/> |Editor opens at Restricted level  <br/> |
|**Domain Trust: Intranet** <br/> |Fails to open  <br/> |Editor opens at Domain level  <br/> |Editor opens at Restricted level  <br/> |
|**Domain Trust: Internet** <br/> |Fails to open  <br/> |Editor opens at Domain level  <br/> |Editor opens at Restricted level  <br/> |
|**Restricted** <br/> |Fails to open  <br/> |Fails to open  <br/> |Editor opens at Restricted level  <br/> |
   
## Specifying a Security Level

The InfoPath form designer automatically selects the appropriate security level (either Restricted or Domain) based on the features that you are using in the form. The security setting is always as restrictive as possible, starting at Restricted, to help ensure a greater level of protection for you and your data. Users can manually override this automated setting to select a level of security that is more appropriate for the form by following these steps:
  
1. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
2. In the **Categories** list, click **Security and Trust**.
    
3. Uncheck the **Automatically determine security level (recommended)** check box. 
    
4. Select the desired security level.
    
## Mail Deployment and Browser-enabled Form Templates

InfoPath allows you to send your form templates as an attachment to an e-mail message and to move them from one location to another. Mail deployment is an easy and effective way to distribute forms for interoffice use and also to deploy forms to remote users.
  
Alternatively, if you have Microsoft SharePoint Server 2010 with InfoPath Forms Services available, you can create form templates that enable users who do not have InfoPath installed to fill out forms in a Web browser.
  
## Understanding Form Identity

All forms in the InfoPath designer are created with an identity. This identity information helps InfoPath associate forms with form templates in the cache and to retrieve updates to forms when they are posted to a shared location. By default, InfoPath creates two identities for form templates: a Form ID and an Access Path. 
  
## Form ID

The Form ID is a unique identifier based on a prefix, the form name, and the form namespace. The identifier should be a unique name that can be used to correctly associate form files with the associated form template in the client computer cache. The Form ID is specified as the name attribute (for example,  `name="urn:MyForm:MyCompany:Template1:myXSD-1583-78-G3V94-23-47"`) in the form definition file (.xsf). 
  
## Access Path

The Access Path is a location identifier that is used to determine the correct location for the form template and also the location to receive updates. When saved or published, where the form template is saved or published becomes the default Access Path. Each time that a form is opened on the client computer, the form attempts to associate itself with a cached form. It will attempt to do this in the following order:
  
1. Look for a fully trusted form template with a matching Form ID.
    
2. Look for a form template in the cache with a matching Access Path.
    
3. Look for a form template in the cache with a matching Form ID.
    
Once matched, the form will open with the associated form template. In cases in which the match was made with an Access Path, InfoPath will use the Access Path to retrieve updates to the form template. This method simplifies enterprise administration, maintenance, and update of forms. In cases in which the match cannot be made and the trust level is Domain, the form will not open. The Access Path is specified as the **publishUrl** attribute in the form definition file (.xsf). 
  
Just as there are two identification properties for each form template, there is a set of heuristics to specifically determine the resulting entries in the cache, based on the condition of the form template (whether it has an Access Path, a Form ID, or both) and the state of the network connection.
  
## Designing a Form to Send as an Attachment to an E-mail Message

All forms that are created in the InfoPath designer can be sent to users as an attachment to an e-mail message. E-mail deployment is an easy and effective way to distribute forms for interoffice use and also to deploy forms to remote users.
  
### To mail a form template to other users

1. Click the **File** tab, click **Publish**, and then click the **E-mail** button. 
    
2. Fill out the next two pages of the **Publishing Wizard** clicking **Next** to continue after each page, and then click **Publish**.
    
3. An e-mail message is displayed enabling you to fill in the list of recipients and any additional instructions that you may have for them.
    
4. After you are finished, click **Send**. The form and the form template will be attached to the message.
    
## E-mail Deployment: Restricted, Domain, and Full Trust Form Templates

E-mail deployment of Restricted form templates allows dynamic forms without data connections to be opened from anywhere. Recipients can open form templates sent as e-mail attachments either directly from Microsoft Outlook 2010 or from wherever the recipient has saved the attachment. Additionally, Outlook 2010 allows users to edit forms directly in the message.
  
Form templates with the Domain trust level must be opened from their published location, but by publishing to a list of e-mail recipients in the **Publishing Wizard**, they can be sent as an attachment to an e-mail message. When the attachment is opened, it functions as a link to the actual published location of the template. The form template at that location is what is actually opened in the InfoPath editor.
  
Using a Domain-level form template sent as an e-mail attachment resembles using any other kind of document; for example, a Microsoft Excel workbook or a Microsoft Word document. A user can just click on the form to open and use it. In addition, all the benefits of Domain-level updates are available to users.
  
You can e-mail form templates that request Full Trust access, but these templates must be signed or they will not be allowed to open. Form templates requesting Domain or Restricted access do not have to be signed to be sent as an e-mail attachment. InfoPath does not check or verify the signature, even if the template is signed, except to see whether it can be updated automatically. You could digitally sign a Domain or Restricted form template and still have automatic update capability. In this case, the digital signature will prevent any cache conflict messages from appearing.
  
## Sharing Forms by E-mail Message or From a Common Shared Location

Certain questions should be considered when you are creating a form that will be deployed by e-mail message.
  
- **Will your form be updated regularly?** If you are developing a form that must be updated regularly, the form should be published to a shared location before it is sent to other users. This practice enables you to update the form by publishing newer versions to the shared location but it also enables you to immediately distribute the form template to users who may not have access to the shared location. 
    
    If a form is updated and then distributed by e-mail message, users will get a cache conflict message when they try to open the new form, if they have an older version stored on their computer and the Access Path has changed. The user will be prompted to choose which version they want to use. Even if the updated form is the same as the one on the user's computer, the user will get a cache conflict message and be prompted to choose which copy they want to use. The best practice to use in the latter case is to share the form from a shared location instead.
    
- **Does your form access a data connection or use other features not supported at the Restricted security level?** If you are developing a form that requires Domain-level security, InfoPath requires you to publish the form to a shared location for users to be able to open it. Because form templates will only open at the security level they request, forms opened directly from an e-mail message will not open if InfoPath cannot grant Domain-level security. 
    
## Benefits of Using Signed Form Templates

- It allows the form template to open with Full Trust security.
    
- It avoids the cache conflict message if the form is moved to a new location.
    
Additionally, if a form template is signed, you get the added benefit of the automatic update functionality. For more information, see [Deploying Signed InfoPath Form Templates](deploying-signed-infopath-form-templates.md).
  
 **Example: Updating Domain or Restricted Templates** The following example shows how an updated, signed form template requesting either Domain or Restricted access can overwrite an older copy: 
  
1. "A" sends a signed form template to "B".
    
2. "B" opens the form template.
    
3. "A" updates the form template (for example, adds more fields).
    
4. "A" sends the updated form template to "B".
    
5. "B" opens the updated form template.
    
 **Example: Deploying Restricted Form Templates on an Extranet**
  
1. Save the Domain form template on a Web site that is running Microsoft SharePoint Foundation 2010.
    
2. Change the form template security level to Restricted.
    
3. Save the form template on your computer desktop.
    
4. Remove the URL (required only if users have access to the original publish location).
    
5. Send the form to users on an extranet.
    
6. Have the users install the form.
    
7. Have users send the form back to you after filling it out.
    
8. Save the form back to the Web site that is running SharePoint Foundation 2010 and relink the form by using the **Relink documents to this Library** option in the **Form Library Settings** page. 
    
## Signature Verification Failure

A signed form template that requests full trust access but for which the signature cannot be authenticated will not open. Signature verification can fail for any of the following reasons:
  
- The root certificate is not in the trusted root certificate store.
    
- The certificate that was used to sign the form template has expired.
    
- The certificate that was used to sign the form template was revoked.
    
- The signature on the form template is corrupted (an indication that the form template was altered after it was signed).
    
If a signed form template requests Domain or Restricted access, InfoPath will not check or verify the signature except to determine whether the template can be updated automatically.
  
## Infrastructure Registry Keys for Form Migration Open Behavior

When a user attempts to open a form, and the form is matched against a form template by its Form ID, InfoPath will display an error message if the form template has a Domain trust level and the domain does not match the  *href*  attribute of the form. This prevents forms from being opened that were not explicitly created by using the form template. 
  
InfoPath does not allow form templates with the same Form ID to coexist. Four additional registry keys help system administrators give users the option of whether to allow the XML file to open against a form template. This model also lets administrators set the open behavior they want for forms.
  
The following table describes the default settings for the registry keys. If these registry keys are absent, the default value specified in the table will be enforced.
  
The Name values correspond to the Internet Explorer domain settings. These values determine the form open behavior in these security zones, either blocking or allowing the opening of the form, or giving the user the option to open the form.
  
|**Name value**|**Block**|**User Interface**|**Allow**|
|:-----|:-----|:-----|:-----|
|**Internet** <br/> |X  <br/> |||
|**Intranet** <br/> ||X  <br/> ||
|**Client Computer** <br/> |||X  <br/> |
|**Trusted Site** <br/> |||X  <br/> |
   
The registry key path is
  
```
HKEY_CURRENT_USER\Software\Microsoft\Office\14.0\InfoPath\Open Behaviors
```

The form open behavior is defined as follows:
  
-  `Block [REG_DWORD = 0]`- An error dialog with a Help button will be shown. InfoPath will not allow the XML file to open when the form is running in the specified security zone and does not match the template domain. 
    
-  `User Interface [REG_DWORD = 1]`- The Yes/No dialog box will be shown. InfoPath will prompt the user to open the XML file against the form template when the form is running in the specified security zone and does not match the template domain. 
    
-  `Allow [REG_DWORD = 2]`- The XML file will open without an error or warning dialog. InfoPath will allow the XML file to open when the form is running in the specified security zone and does not match the template domain. 
    
If a form is opened against a form template running at the Domain security level, and the security domain of the template's "cached from" location (that is, where the form is cached from) and the form's **href** attribute do not match, InfoPath will check the registry to define the form open behavior. Allowed behavior will be based on the security zone in which the template is located (the  *CachedFromLocation*  value). 
  
For example, when a form matches a form template based on Form ID but not on Access Path, and the form template is cached from an Internet location, InfoPath will show an error dialog with a Help button.
  
> [!NOTE]
> InfoPath forms will not open when the domain is an Internet Explorer Restricted domain; therefore, there is no registry key for Internet Explorer Restricted Sites. 
  

