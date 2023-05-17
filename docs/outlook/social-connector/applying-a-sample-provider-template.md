---
title: "Applying a Sample Provider Template"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: da487569-f2f0-404c-b944-38ed1c1b82bb
description: "The sample Outlook Social Connector (OSC) provider templates give you a framework for implementing an OSC provider. "
---

# Applying a Sample Provider Template

The sample Outlook Social Connector (OSC) provider templates give you a framework for implementing an OSC provider. The provider templates are available in C++, C#, and Visual Basic. These templates are just a starting point for your provider development; the templates do not address writing the implementation code for the provider and creating a setup package for the provider. The following procedure shows how to apply an OSC provider template when you begin to develop a provider.
  
### To apply an OSC provider template

1. On the **Start** menu, right-click **Microsoft Visual Studio 2010** and click the **Run as administrator** command. When prompted, click **Yes** to run Visual Studio as an administrator.

2. Change the project name and namespace in the template to your project name and namespace identifiers.

3. Modify the **AssemblyInfo** class to specify the appropriate assembly information.

4. Implement the interface members marked as **To-Do** and add more dependencies and references, as required.

5. Build the project.

6. Ensure that the provider assembly ProgID is listed as a key under `HKEY_CURRENT_USER\Software\Microsoft\Office\Outlook\SocialConnector\SocialProviders`.

7. To distribute the setup project, create a setup project in Visual Studio or a setup tool of your choice.

8. Your setup project should complete COM registration for your assembly and also create the ProgID key as listed in step 5.

## See also

- [Downloading the Samples](downloading-the-samples.md)
- [OSC Sample Templates](osc-sample-templates.md)
