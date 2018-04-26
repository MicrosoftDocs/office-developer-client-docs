---
title: "PageSize Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: da56edd8-8947-aeff-2ef5-a8535c66575b

---

# PageSize Property (ADO)

Indicates how many records constitute one page in the [Recordset](recordset-object-ado.md).
  
## Settings and Return Values

Sets or returns a **Long** value that indicates how many records are on a page. The default is 10. 
  
## Remarks

Use the **PageSize** property to determine how many records make up a logical page of data. Establishing a page size allows you to use the [AbsolutePage](absolutepage-property-ado.md) property to move to the first record of a particular page. This is useful in Web server scenarios when you want to allow the user to page through data, viewing a certain number of records at a time. 
  
This property can be set at any time, and its value will be used for calculating the location of the first record of a particular page.
  

