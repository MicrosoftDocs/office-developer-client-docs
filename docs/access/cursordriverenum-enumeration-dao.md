---
title: "CursorDriverEnum Enumeration (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: d0312ece-c30a-7d61-d5f3-75edf0d0afc8
description: "Specifies the type of cursor driver."
---

# CursorDriverEnum Enumeration (DAO)

Specifies the type of cursor driver.
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbUseClientBatchCursor** <br/> |3  <br/> |Always uses the FoxPro Cursor Library. This option is required for performing batch updates.  <br/> |
|**dbUseDefaultCursor** <br/> |-1  <br/> |(Default) Uses server-side cursors if the server supports them; otherwise uses the ODBC Cursor Library.  <br/> |
|**dbUseNoCursor** <br/> |4  <br/> |Opens all cursors (that is, **Recordset** objects) as forward-only type, read-only, with a rowset size of 1. Also known as "cursorless queries."  <br/> |
|**dbUseODBCCursor** <br/> |1  <br/> |Always uses the ODBC Cursor Library. This option provides better performance for small result sets, but degrades quickly for larger result sets.  <br/> |
|**dbUseServerCursor** <br/> |2  <br/> |Always uses server-side cursors. For most large operations this option provides better performance, but might cause more network traffic.  <br/> |
   

