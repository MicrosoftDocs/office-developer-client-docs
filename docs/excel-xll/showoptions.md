---
title: "ShowOptions"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 51acac58-ec39-488f-979c-1887dc2ab94b
description: "Applies to: Excel 2013 | Office 2013 | Visual Studio"
---

# ShowOptions

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Shows a modal dialog box to collect information from the user. This entry point is called when a user clicks the **Options** button next to the **Cluster type** box for the selected cluster connector in the **Excel Options** dialog box (in the **Advanced** category under the **Formulas** section). Cluster connectors are responsible for implementing their own options dialog interface and for storing the related data in the registry or elsewhere. The options are internal to the cluster connector. Excel is not aware of them. 
  
```cs
int ShowOptions(HWND hWndParent)
```

## Parameters

 _hWndParent_
  
> A handle to the Excel window.
    
## Return Value

 **xlHpcRetSuccess** if the dialog box was shown; **xlHpcRetCallFailed** if it was not shown. 
  
## Remarks

Cluster connectors can use this dialog box to get information, such as what cluster server to use, from the user.
  
## See also

#### Concepts

[Excel Cluster Connector Functions](excel-cluster-connector-functions.md)

