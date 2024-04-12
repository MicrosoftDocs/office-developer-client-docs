---
title: "Automating InfoPath from an external application"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: 4d2248d9-ab20-bcaa-d75b-62876c5e95eb
description: "Microsoft InfoPath provides application automation from code written using COM and script by using methods of the Application object and the XDocuments collection."
---

# Automating InfoPath from an external application

Microsoft InfoPath provides application automation from code written using COM and script by using methods of the **Application** object and the **XDocuments** collection. 
  
## Overview of the Application and XDocument Objects

The **Application** object contains the following methods used for automation: 
  
|**Method**|**Description**|
|:-----|:-----|
|**CacheSolution** <br/> |Examines the in the cache and, if necessary, updates it from the published location of the form template. |
|**Quit** <br/> |Quits the Microsoft Office InfoPath application. |
|**RegisterSolution** <br/> |Installs the specified Microsoft Office InfoPath form template. |
|**UnregisterSolution** <br/> |Uninstalls the specified Microsoft Office InfoPath form template. |
   
The **XDocuments** collection contains the following methods that can be used for external automation: 
  
|**Method**|**Description**|
|:-----|:-----|
|**Close** method  <br/> |Closes the specified Microsoft Office InfoPath form. |
|**New** method  <br/> |Creates a new Microsoft Office InfoPath form. |
|**NewFromSolution** method  <br/> |Creates a new Microsoft Office InfoPath form based on the specified form template. |
|**NewFromSolutionWithData** method  <br/> |Creates a new Microsoft Office InfoPath form using the specified XML data and form template. |
|**Open** method  <br/> |Opens the specified Microsoft Office InfoPath form. |
   
To use the **Application** object from an external application, you use the **CreateObject** function with the ProgID of the InfoPath application ("InfoPath.Application") to create an object variable that represents the InfoPath application. You can then use the **XDocuments** property to access the **XDocuments** collection and use its methods to open or create an InfoPath form. The following example demonstrates the creation of a reference to the **Application** object using the Microsoft Visual Basic 6.0 or Visual Basic for Applications (VBA) programming language: 
  
```vb
Dim objIP As Object 
 
Set objIP = CreateObject("InfoPath.Application") 
 
' Open an existing form 
objIP.XDocuments.Open ("C:\MyFolder\MyForm.xml") 
 
' Create a new form based on a form template 
objIP.XDocuments.NewFromSolution ("C:\MyFolder\MyForm.xsn") 

```

> [!NOTE]
> Because the **CreateObject** function creates an object variable using late binding, automatic statement completion will not be available in the Visual Basic Editor. Refer to the links in the preceding tables for information about the correct calling syntax. 
  

