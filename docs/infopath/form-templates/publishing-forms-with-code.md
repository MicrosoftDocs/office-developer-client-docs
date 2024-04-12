---
title: "Publishing Forms with Code"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
 
 
ms.localizationpriority: medium
ms.assetid: caafab24-6413-4731-813d-cba3ae9ea97e
description: "Any site collection administrator can publish forms with code directly from the InfoPath Designer publishing wizard to a form library on SharePoint. The code is executed in a sandboxed environment so that malicious code cannot harm the server. This is referred to as publishing a sandboxed solution or publishing to the SharePoint sandbox infrastructure."
---

# Publishing Forms with Code

Any site collection administrator can publish forms with code directly from the InfoPath Designer publishing wizard to a form library on SharePoint. The code is executed in a sandboxed environment so that malicious code cannot harm the server. This is referred to as publishing a sandboxed solution or publishing to the SharePoint sandbox infrastructure.
  
InfoPath 2010 and SharePoint Server 2010 also support administrator-deployed solutions. A form designer publishes forms with code to a local store which are later reviewed and uploaded by a SharePoint farm administrator. The code is given full trust, and can incorporate functionality requiring elevated privileges such as file IO.
  
## Comparing Sandboxed and Administrator-approved Solutions

The following table summarizes the differences between publishing sandboxed and administrator-approved solutions. 
  
||**Sandboxed Solutions**|**Administrator-approved Solutions**|
|:-----|:-----|:-----|
|**Permissions Required** <br/> |Can be published by any site collection administrator. |Can be deployed by a farm administrator. |
|**Publishing** <br/> |Can be published directly from InfoPath. |Can be deployed using Central Administration or the stsadm command-line tool. |
|**Protection** <br/> |Code is run in a sandboxed environment. This helps protect the server from malicious code. |Code can run with full trust and access any resource on the server. |
|**Recommended Use** <br/> |Forms that only require a small amount of code. |Forms that contain many lines of code. |
   
### Publishing Form Templates as Sandboxed Solutions

Publishing a form with code as a sandboxed solution is no different from publishing any other form to a document library. Just use the publishing wizard as usual and your form will be uploaded to the server and will operate in the sandbox.
  
Note that there are certain restrictions to deploying your form as a sandboxed solution:
  
- Must be an InfoPath form.
    
- Must use C# or Visual Basic as the programming language.
    
- Cannot submit to email data connections.
    
- Cannot have properties promoted for part-to-part connections.
    
- Must not have any managed meta-data controls or data connections.
    
To enable site collection administrators to use sandboxed solutions on Microsoft SharePoint Server 2010 or a server that runs Microsoft SharePoint Foundation 2010, the farm administrator must start the Windows SharePoint User Code service.
  
### To start the Windows SharePoint User Code service

1. Open Central Administration.
    
2. Under **System Services**, click **Manage services on server**.
    
3. Start the **Microsoft SharePoint Foundation User Code Service**.
    
### To publish a sandboxed solution

1. Open the form template in the InfoPath designer.
    
2. Click the **File** tab, and then click **SharePoint Server** on the **Publish** tab in the Backstage. 
    
3. Enter the URL of the SharePoint site to publish to, and then click **Next**. 
    
    > [!IMPORTANT]
    > You must be a site collection administrator on this site to publish this form template as a sandboxed solution. 
  
4. Select **Form Library**, and then click **Next**.
    
5. Select **Create a new form library**, and then click **Next**.
    
6. Enter the name and descriptions for your form library, and then click **Next**.
    
7. Click **Publish**.
    
For example solutions that demonstrate scenarios that are appropriate for form templates published as sandboxed solutions, see [Sample Sandboxed Solutions](sample-sandboxed-solutions.md).
  
### Publishing Form Templates as Administrator-Deployed Solutions

Publishing your form as an administrator-approved template is recommended if your form has many data connections, if it requires full-trust security, or if you require a farm-wide template.
  
There are several steps that a farm administrator must complete before an administrator-deployed solution is available on SharePoint, and you as the developer must prepare the solution before the administrator is engaged.
  
First, if your form is going to be deployed as full trust, you must set the security level as described in the following procedure.
  
### To set the security level of a form template to full trust

1. Open the form template in the InfoPath designer.
    
2. Click the **File** tab, on the **Info** tab click **Form Options**.
    
3. Click the **Security and Trust** category, and then clear the **Automatically determine security level** check box. 
    
4. Select **Full Trust**.
    
Then, publish the form by using the following procedure, but be aware that there are some differences from a standard publishing procedure.
  
### To publish an administrator-deployed solution

1. In the first page of the **Publishing Wizard**, specify the location of the SharePoint Server 2010 or SharePoint Foundation 2010 site, and then click **Next**.
    
2. InfoPath will automatically select the **Administrator-approved form template** check box on the second page of the wizard. Click **Next**.
    
3. The third page is unique to administrator-deployed scenarios. Instead of selecting a SharePoint Server, publish the form to a local store. The SharePoint administrator will upload the file from this location during the administrator deployment process.
    
4. Complete the remaining pages of the **Publishing Wizard**.
    

