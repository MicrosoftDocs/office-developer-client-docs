---
title: "About the InfoPath XML interop assembly"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
keywords:
- msxml interop [infopath 2007],InfoPath 2007, XML primary interop assembly,InfoPath XML interop assembly
ms.localizationpriority: medium
ms.assetid: fb28659b-8a71-4f43-9121-2c748fb2c5e1
description: "The InfoPath XML interop assembly is provided to allow support for interoperability between managed code and the COM server exposed by Microsoft XML Core Services (MSXML) from external applications that automate InfoPath."
---

# About the InfoPath XML interop assembly

The InfoPath XML interop assembly is provided to allow support for interoperability between managed code and the COM server exposed by Microsoft XML Core Services (MSXML) from external applications that automate InfoPath.

The **.NET Programmability Support** option in the InfoPath setup program installs three interop assemblies. Interop assemblies are .NET assemblies that act as a bridge between managed and unmanaged code, mapping COM object members to equivalent .NET managed members. One of those assemblies, Microsoft.Office.Interop.InfoPath.Xml.dll, provides the members of the [Microsoft.Office.Interop.InfoPath.Xml](/dotnet/api/microsoft.office.interop.infopath.xml?view=infopath-external) namespace, which is used to work with members exposed by the COM server for Microsoft XML Core Services (MSXML) from external applications that automate InfoPath using managed code. 
  
> [!NOTE]
> The references to the Microsoft.Office.Interop.InfoPath.dll and Microsoft.Office.Interop.InfoPath.Xml.dll interop assemblies that are required for InfoPath external automation projects must be established manually. For more information on external automation, see [External Automation Scenarios and Examples](external-automation-scenarios-and-examples.md). 
  
## See also

- [Working with MSXML and System.Xml Using the InfoPath 2003 Object Model](https://msdn.microsoft.com/library/f7a0cac5-26f9-49ed-b52c-0240ef0c9d38%28Office.15%29.aspx)

