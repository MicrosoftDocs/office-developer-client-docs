---
title: "NumericScale Property (ADOX)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ebe73bdc-2570-f54a-3d2f-85a2a4634c9a

---

# NumericScale Property (ADOX)

Indicates the scale of a numeric value in the column.
  
## Settings and Return Values

Sets and returns a **Byte** value that is the scale of data values in the column when the [Type](http://msdn.microsoft.com/library/3e222e89-f57e-28f9-8488-81828f882643%28Office.15%29.aspx) property is **adNumeric** or **adDecimal**. **NumericScale** is ignored for all other data types. 
  
## Remarks

The default value is zero (0).
  
 **NumericScale** is read-only for [Column](column-object-adox.md) objects already appended to a collection. 
  

