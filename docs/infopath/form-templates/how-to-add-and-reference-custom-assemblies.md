---
title: "Add and Reference Custom Assemblies"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
 
keywords:
- infopath 2003-compatible form templates, using custom assemblies,assemblies [InfoPath 2007], adding custom using InfoPath 2003 object model
 
ms.localizationpriority: medium
ms.assetid: 20e1f43e-8279-48fc-8f34-16a2729dbc9b
description: "When you add a reference to a custom assembly in a managed-code form template project, that assembly is included within the form template file (.xsn) when your project is compiled and published."
---

# Add and Reference Custom Assemblies

When you add a reference to a custom assembly in a managed-code form template project, that assembly is included within the form template file (.xsn) when your project is compiled and published.
  
## Add and Reference a Custom Assembly

To avoid a conflict with how the InfoPath project system manages files that are added to the form template file, do not copy any custom assemblies that you want to reference into the top-level folder of a form template project. By default, this will be a path in the following format: < *drive* >:\Users\  *UserName*  \Documents\InfoPath Projects\  *ProjectName* 
  
If you do want to move custom assemblies that you reference to a location within the project folder, you must create a subfolder under the main project folder, and then copy and reference custom assemblies from that subfolder. However, be aware that creating a subfolder for referenced assemblies is not necessary. As long as a referenced assembly is not located within the project's top-level folder, the InfoPath project system will copy the assembly into the form template file (.xsn) when the project is compiled and published.
  
### Reference a custom assembly from its default location

1. Open the form template project in Visual Studio 2012.
    
2. On the **Project** menu, click **Add Reference**.
    
3. Click the **Browse** tab, locate and specify the assembly, and then click **OK** to add the reference. 
    
## See also

#### Tasks

[Create a Form Template Using the InfoPath 2003 Object Model](how-to-create-a-form-template-using-the-infopath-2003-object-model.md)

