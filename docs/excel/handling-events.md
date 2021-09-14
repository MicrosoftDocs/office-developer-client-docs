---
title: "Handling Events"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
 
ms.localizationpriority: medium
ms.assetid: b67fcb83-a0e2-4349-88f5-bcc181306eac
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# Handling Events

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Starting in Excel 2010, XLLs can receive events designed to manage the asynchronous function life cycle. The events are as follows:
  
- **CalculationEnded**: Raised when Excel is finished calculating. After this event, you can free resources allocated during the calculation.
    
- **CalculationCanceled**: Raised when the user interrupts the calculation. The XLL stops any asynchronous activities. Immediately following this event, the **CalculationEnded** event is raised. 
    
To handle these events, the XLL uses the C API function [xlEventRegister](xleventregister.md). 
  
> [!NOTE]
> **CalculationEnded** and **CalculationCanceled** are not raised during programmatic recalculation. 
  

