---
title: "Bookmark Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 101b2ce1-21d8-aa79-e530-20f9d1c73fc8
---

# Bookmark Property (ADO)

Indicates a bookmark that uniquely identifies the current record in a [Recordset](recordset-object-ado.md) object or sets the current record in a **Recordset** object to the record identified by a valid bookmark. 
  
## Settings and Return Values

Sets or returns a **Variant** expression that evaluates to a valid bookmark. 
  
## Remarks

Use the **Bookmark** property to save the position of the current record and return to that record at any time. Bookmarks are available only in **Recordset** objects that support bookmark functionality. 
  
When you open a **Recordset** object, each of its records has a unique bookmark. To save the bookmark for the current record, assign the value of the **Bookmark** property to a variable. To quickly return to that record at any time after moving to a different record, set the **Recordset** object's **Bookmark** property to the value of that variable. 
  
The user may not be able to view the value of the bookmark. Also, users should not expect bookmarks to be directly comparable — two bookmarks that refer to the same record may have different values.
  
If you use the [Clone](clone-method-ado.md) method to create a copy of a **Recordset** object, the **Bookmark** property settings for the original and the duplicate **Recordset** objects are identical and you can use them interchangeably. However, you cannot use bookmarks from different **Recordset** objects interchangeably, even if they were created from the same source or command. 
  
 **Remote Data Service Usage** When used on a client-side **Recordset** object, the **Bookmark** property is always available. 
  

