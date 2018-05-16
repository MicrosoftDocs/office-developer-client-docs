---
title: "Troubleshoot form templates that use the InfoPath object model at run time"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
keywords:
- troubleshooting form templates [infopath 2007], run time,InfoPath 2003-compatible form templates, troubleshooting at run time
localization_priority: Normal
ms.assetid: 65e7882e-6397-4375-9bb4-d993d700d749
description: "The following sections describe common troubleshooting scenarios you may encounter while working with InfoPath managed-code form templates that use the InfoPath 2003-compatible object model provided by the Microsoft.Office.Interop.InfoPath.SemiTrust namespace at run time."
---

# Troubleshoot form templates that use the InfoPath object model at run time

The following sections describe common troubleshooting scenarios you may encounter while working with InfoPath managed-code form templates that use the InfoPath 2003-compatible object model provided by the **Microsoft.Office.Interop.InfoPath.SemiTrust** namespace at run time. 
  
## Display Notifications for Unhandled Managed-Code Exceptions at Run Time

If you do not use try-catch exception handling in your form code, InfoPath will display information about unhandled exceptions in the InfoPath error dialog box while debugging and previewing. However, by default, unhandled exceptions are not displayed in the InfoPath error dialog box at run time when you deploy your managed-code form template. If you want managed-code exceptions displayed at run time, follow the procedure in the "Handling Managed Code Exceptions" section of [Handle Errors Using the InfoPath 2003 Object Model](how-to-handle-errors-using-the-infopath-2003-object-model.md).
  
## Problems with Managed-Code Form Templates after Deployment

Be sure to test your managed-code form template in the location where it will be finally deployed. For information on deployment procedures, see [Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md). For information on security scenarios that affect deployment, see [About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md).
  
If you use the .NET Framework 1.1 Configuration utility and the InfoPath Form Templates code group to add specific permissions for a managed-code form template, make sure that the same security policy is deployed on all client computers. Also, if you are specifying **URLEvidence** that refers to a location on the local computer, make sure that the specified location refers to the folder where the solution will be finally deployed (not the same location used during development). For information on configuring .NET Framework security settings for a managed-code form template, see the "Assigning FullTrust to Forms at a Specific URL or UNC" section of the [Configure Security Settings for Form Templates with Code](how-to-configure-security-settings-for-form-templates-with-code.md) topic. 
  
## See also

#### Concepts

[About the Security Model for Form Templates with Code](about-the-security-model-for-form-templates-with-code.md)
  
[Deploy InfoPath Form Templates with Code](how-to-deploy-infopath-form-templates-with-code.md)
  
[Handle Errors Using the InfoPath 2003 Object Model](how-to-handle-errors-using-the-infopath-2003-object-model.md)
  
[Debug InfoPath Projects Using the InfoPath 2003 Object Model](how-to-debug-infopath-projects-using-the-infopath-2003-object-model.md)

