---
title: "HYPERLINK Function"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251441
 
localization_priority: Normal
ms.assetid: 943636a6-e135-a626-7924-11e238156548
description: "Navigates to the specified address, which can be a file, UNC, or URL path."
---

# HYPERLINK Function

Navigates to the specified address, which can be a file, UNC, or URL path.
  
## Syntax

HYPERLINK(" ** *address* ** "[," ** *subaddress* ** "," ** *extrainfo* ** ", ** *window* **," ** *frame* ** "]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _address_ <br/> |Required  <br/> |**String** <br/> |A full path or a relative path.  <br/> |
| _subaddress_ <br/> |Optional  <br/> |**String** <br/> |Specifies a location within address to link to. For example, if address is a Microsoft Visio file, subaddress can be a page name; if a Microsoft Excel file, subaddress can be a worksheet or range within a worksheet; if a URL for an HTML page, subaddress can be an anchor.  <br/> |
| _extrainfo_ <br/> |Optional  <br/> |**String** <br/> |Passes information used in resolving the URL, such as the coordinates of an image map.  <br/> |
| _window_ <br/> |Optional  <br/> |**Boolean** <br/> |Specifies whether the hyperlink is opened in a new window. The default value is FALSE.  <br/> |
| _frame_ <br/> |Optional  <br/> |**String** <br/> | Specifies the name of a frame to target when Visio is open as an Active document in an ActiveX browser, such as Microsoft Internet Explorer 3.0 or later. The default is an empty string.  <br/> |
   
## Remarks

If the document has no base path, Visio navigates according to the document path. If the document has not been saved, the hyperlink is undefined. 
  
Relative paths are based on the **Hyperlink base** field specified in the **Visio Properties** dialog box. 
  
You can use the GOTOPAGE function to navigate to pages of a document. 
  
## Example 1

 `HYPERLINK("C:\My Documents\Drawing1.vsdx")`
  
## Example 2

 `HYPERLINK("\\Server\Share\Drawing1.vsdx")`
  
## Example 3

 `HYPERLINK("http://www.microsoft.com")`
  
## Example 4

 `HYPERLINK("..\data.xlsx","sheet1!A1")`
  

