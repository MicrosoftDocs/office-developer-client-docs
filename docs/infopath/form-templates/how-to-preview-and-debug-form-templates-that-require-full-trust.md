---
title: "Preview and Debug Form Templates that Require Full Trust"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- debugging [infopath 2007], infopath 2003-compatible form templates,previewing InfoPath 2003-compatible form templates,form templates [InfoPath 2007], previewing 2003-compatible,form templates [InfoPath 2007], debugging 2003-compatible,debugging InfoPath 2003-compatible form templates
 
localization_priority: Normal
ms.assetid: 5c491666-06f0-42ec-967e-1c70cd5e03a0
description: "By default, if you attempt to debug or preview a managed-code project that contains code that invokes an object model member that requires full trust, such as the LoginName property which requires access to information about the user's login domain, Microsoft InfoPath will display the following error messages."
---

# Preview and Debug Form Templates that Require Full Trust

By default, if you attempt to debug or preview a managed-code project that contains code that invokes an object model member that requires full trust, such as the **LoginName** property which requires access to information about the user's login domain, Microsoft InfoPath will display the following error messages. 
  
When previewing:
  
"An unhandled exception has occurred in the form's code." Followed by, "InfoPath cannot complete this action, because of an error in the form's code."
  
When debugging:
  
Focus will move to the line of code in the code editor that is calling the member that requires full trust, and the following message will be displayed: " **SecurityException** was unhandled by user code - Request failed". 
  
To allow the form template's business logic to call this member when it is being debugged or previewed, you must set your form template's security level to **Full Trust** as described in the following procedure. 
  
## Configuring a Managed Code Form Template that Requires Full Trust

### Set your form's security level to Full Trust

1. In InfoPath, open the form template in design mode.
    
2. Click the **File** tab, and then click **Form Options** on the **Info** tab. 
    
3. In the **Category** list, click **Security and Trust.**
    
4. Under **Security Level**, clear **Automatically determine security level**.
    
5. Select **Full Trust**, and then click **OK**.
    
After this procedure is performed, you can debug your project as described in [Preview and Debug InfoPath Form Templates with Code](how-to-preview-and-debug-infopath-form-templates-with-code.md).
  
> [!NOTE]
> Successfully deploying a managed code form template that requires full trust requires additional steps, such as digitally signing, or installing and registering the form template. For information on deploying a managed code form template after it is debugged see, [Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md). 
  
## See also

#### Concepts

[Preview and Debug InfoPath Form Templates with Code](how-to-preview-and-debug-infopath-form-templates-with-code.md)
  
[Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md)

