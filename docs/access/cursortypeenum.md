---
title: "CursorTypeEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 7c5fa8b2-85ea-a0a7-41f1-a78650aced3e
---

# CursorTypeEnum

Specifies the type of cursor used in a [Recordset](recordset-object-ado.md) object. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adOpenDynamic** <br/> |2  <br/> |Uses a dynamic cursor. Additions, changes, and deletions by other users are visible, and all types of movement through the **Recordset** are allowed, except for bookmarks, if the provider doesn't support them.  <br/> |
|**adOpenForwardOnly** <br/> |0  <br/> |Default. Uses a forward-only cursor. Identical to a static cursor, except that you can only scroll forward through records. This improves performance when you need to make only one pass through a **Recordset**.  <br/> |
|**adOpenKeyset** <br/> |1  <br/> |Uses a keyset cursor. Like a dynamic cursor, except that you can't see records that other users add, although records that other users delete are inaccessible from your **Recordset**. Data changes by other users are still visible.  <br/> |
|**adOpenStatic** <br/> |3  <br/> |Uses a static cursor. A static copy of a set of records that you can use to find data or generate reports. Additions, changes, or deletions by other users are not visible.  <br/> |
|**adOpenUnspecified** <br/> |-1  <br/> |Does not specify the type of cursor.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.CursorType.DYNAMIC  <br/> |
|AdoEnums.CursorType.FORWARDONLY  <br/> |
|AdoEnums.CursorType.KEYSET  <br/> |
|AdoEnums.CursorType.STATIC  <br/> |
|AdoEnums.CursorType.UNSPECIFIED  <br/> |
   

