---
title: "Configure Security Settings for Form Templates with Code"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- security policy deployment package [infopath 2007],URLs [InfoPath 2007], assigning FullTrust,code access security [InfoPath 2007],UNCs [InfoPath 2007], assigning FullTrust,CAS [InfoPath 2007],security [InfoPath 2007], configuring,code groups [InfoPath 2007],FullTrust [InfoPath 2007], assigning to UNCs,FullTrust [InfoPath 2007], assigning to URLs
 
localization_priority: Normal
ms.assetid: 24d1a322-581f-497e-b97b-bd02c4516551
description: "You can customize the permission set that is applied to an InfoPath managed code form template by using the .NET Configuration snap-in."
---

# Configure Security Settings for Form Templates with Code

You can customize the permission set that is applied to an InfoPath managed code form template by using the .NET Configuration snap-in.
  
The common language runtime (CLR) hosted by InfoPath will look for a predefined code group named  *InfoPath Form Templates*  at the Machine policy level under the All_Code group. The CLR will apply the permission sets that are defined under that group to the application domain (AppDomain) where the form code runs. This enables you to customize the permission sets that are granted to InfoPath managed code form templates. For example, you can grant a form template downloaded from http://MySite permission to access the Active Directory. 
  
For custom security policy defined by using the .NET Configuration snap-in to be applied, it must be deployed on all the client computers where the form template will run.
  
For more information about the security model for InfoPath managed code form templates, see [About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md)
  
## Creating a Code Group for InfoPath Form Templates

The following procedure will create a code group that grants no permissions to InfoPath managed code form templates (except those that are installed or registered on your local computer) under which you can assign permission sets to InfoPath form templates located at specific URLs or UNCs. For information about how to create and assign permission sets to code groups within the  `InfoPath Form Templates` code group, see the following procedure. 
  
> [!NOTE]
> Unlike the **Microsoft .NET Framework 1.1 Configuration** tool that is installed with the Microsoft .NET Framework 1.1 Redistributable Package, the **Microsoft .NET Framework 2.0 Configuration** is installed only with the Microsoft .NET Framework 2.0 Software Development Kit (SDK). 
  
### To create a custom security code group for InfoPath managed code forms

1. From the **Start** menu, point to **Administrative Tools**, and then click **Microsoft .NET Framework 2.0 Configuration**.
    
    If you do not have **Administrative Tools** on the **Start** menu, from the **Control Panel** open **Administrative Tools**, and then double-click **Microsoft .NET Framework 2.0 Configuration**.
    
2. Under **My Computer**, expand the **Runtime Security Policy** node, the **Machine** node, **Code Groups** node, the **All_Code** node, and then right-click the **All_Code** node and click **New** to open the **Create Code Group** dialog box. 
    
3. Name the new code group  `InfoPath Form Templates` (this text must be exact), and then click **Next**.
    
4. Set the condition type for the code group to **All Code**, and then click **Next**.
    
5. Click **Use existing permission set**, assign the **Nothing** permission set to the code group, click **Next**, and then click **Finish**.
    
6. To apply the new settings, close and restart InfoPath.
    
If you prefer, you can manage the permission set for all InfoPath managed code form templates by assigning a permission set other than the **Nothing** permission set to the **InfoPath Form Templates** code group. 
> [!NOTE]
> You can change the permission set for a security code group at any time by right-clicking the group in the . **NET Configuration 2.0** snap-in, clicking **Properties**, and then clicking the **Permission Set** tab. 
  
## Assigning FullTrust to Forms at a Specific URL or UNC

You can create code groups under the **InfoPath Form Templates** group to grant the full trust permission set to form templates from a particular URL or UNC location. After doing this, every form template published to the specified location will run fully trusted. 
  
> [!NOTE]
> A form template that is loaded from the local computer (My Computer Zone code group) is loaded by InfoPath using a random URL. For this reason, you cannot use the following procedure to grant the FullTrust permission set to such a form template. To grant a locally installed form template the FullTrust permission set, use one of the procedures that are described in the "Deploying Form Templates That Require Full Trust" section of the [Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md) topic. 
  
### To assign FullTrust to InfoPath forms at a specific URL or UNC location

1. From the **Start** menu, point to **Administrative Tools**, and then click **Microsoft .NET Framework 2.0 Configuration**.
    
    If you do not have **Administrative Tools** on the **Start** menu, from the **Control Panel** open **Administrative Tools**, and then double-click **Microsoft .NET Framework 2.0 Configuration**.
    
2. Under **My Computer**, expand the **Runtime Security Policy** node, the **Machine** node, **Code Groups** node, the **All_Code** node, and then click the **InfoPath Form Templates** node. 
    
3. In **Tasks** list in the right pane, click **Add a Child Code Group**, name the code group, and then click **Next**.
    
4. In the **Choose the condition type for this code group** list, select **URL**, and then enter the URL or UNC for the location of the InfoPath managed code form templates that you want to grant the **FullTrust** permission set. 
    
    To restrict the permission set to a single form template, specify the full path of that particular form template. For example:
    
     `\\MyServer\MyShare\MyFormTemplate.xsn`
    
     `http://MySite/MySubsite/MyFormTempate.xsn`
    
    To grant the permission set to all form templates in a URL or UNC, omit the name of the template and add an asterisk at the end of the URL or UNC. For example:
    
     `\\MyServer\MyShare\*`
    
     `http://MySite/MySubsite/*`
    
5. Click **Next**, and then click **Use existing permission set** and assign the **FullTrust** permission set to the code group. 
    
6. Click **Next**, and then click **Finish**.
    
7. To apply the new settings, close and restart InfoPath.
    
> [!NOTE]
> To apply a more restrictive or custom permission set, select the appropriate option instead of **FullTrust** in step 4. 
  
## Creating a Deployment Package for InfoPath Security Policy

After defining custom security policy for InfoPath managed-form templates, you can create a Windows Installer Package (.msi) to deploy this security policy on users' computers by using Group Policy or Microsoft Systems Management Server.
  
### To create a deployment package for custom InfoPath security policy

1. From the **Start** menu, point to **Administrative Tools**, and then click **Microsoft .NET Framework 2.0 Configuration**.
    
    If you do not have **Administrative Tools** on the **Start** menu, from the **Control Panel** open **Administrative Tools**, and then double-click **Microsoft .NET Framework 2.0 Configuration**.
    
2. Right-click **Runtime Security Policy**, and then click **Create Deployment Package**.
    
3. Under **Select the security policy to deploy**, click **Machine**, specify the folder and file name for the Windows Installer Package, and then click **Next**.
    
4. Click **Finish** to create the deployment package. 
    
5. For information about how to use the .NET Framework Configuration tool, search Visual Studio Help or the MSDN Web site for ".NET Framework Configuration Tool (Mscorcfg.msc)".
    
## See also



[About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md)

