---
title: "Hosting InfoPath as an XML Editor in Another Application"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: ae24b317-f486-763a-7009-e32c5cb85b59
description: "The Microsoft InfoPath form editing environment can be hosted in a custom Windows application, which enables developers to integrate the InfoPath form editing environment into line-of-business applications."
---

# Hosting InfoPath as an XML Editor in Another Application

The Microsoft InfoPath form editing environment can be hosted in a custom Windows application. This feature enables developers to integrate the InfoPath form editing environment into line-of-business applications. Developers writing traditional COM-based applications can use the **InfoPathEditorObject** object that is available by referencing the IPEDITOR.DLL, and developers writing Microsoft .NET-based applications can use the **Microsoft.Office.InfoPath.FormControl** assembly, which provides managed types based on the COM interface. The IPEDITOR.DLL and **Microsoft.Office.InfoPath.FormControl** assembly are both installed along with InfoPath in the C:\Program Files\Microsoft Office\Office15 or C:\Program Files (x86)\Microsoft Office\Office15 folder. 
  
The MSDN article, Hosting the InfoPath 2007 Form Editing Environment in a Custom Windows Form Application, focuses on the **FormControl** object and how to incorporate it into your custom .NET-based applications. The download associated with the article contains a custom application that provides .NET functions for replicating the InfoPath form editing environment through the use of COM **IOleCommandTargets**.
  

