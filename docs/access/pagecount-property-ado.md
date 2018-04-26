---
title: "PageCount Property (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 9cd8bf5c-b1e7-a453-4629-9cba7e408f53

---

# PageCount Property (ADO)

Indicates how many pages of data the [Recordset](recordset-object-ado.md) object contains. 
  
## Return Value

Returns a **Long** value that indicates the number of pages in the **Recordset**. 
  
## Remarks

Use the **PageCount** property to determine how many pages of data are in the **Recordset** object.  *Pages*  are groups of records whose size equals the [PageSize](pagesize-property-ado.md) property setting. Even if the last page is incomplete because there are fewer records than the **PageSize** value, it counts as an additional page in the **PageCount** value. If the **Recordset** object does not support this property, the value will be -1 to indicate that the **PageCount** is indeterminable. 
  
See the **PageSize** and [AbsolutePage](absolutepage-property-ado.md) properties for more on page functionality. 
  

