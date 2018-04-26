---
title: "CursorOptionEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 3c118c08-02f2-5290-1cef-29e97c35fddc
---

# CursorOptionEnum

Specifies what functionality the [Supports](supports-method-ado.md) method should test for. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adAddNew** <br/> |0x1000400  <br/> |Supports the [AddNew](addnew-method-ado.md) method to add new records.  <br/> |
|**adApproxPosition** <br/> |0x4000  <br/> |Supports the [AbsolutePosition](absoluteposition-property-ado.md) and [AbsolutePage](absolutepage-property-ado.md) properties.  <br/> |
|**adBookmark** <br/> |0x2000  <br/> |Supports the [Bookmark](bookmark-property-ado.md) property to gain access to specific records.  <br/> |
|**adDelete** <br/> |0x1000800  <br/> |Supports the [Delete](delete-method-ado-recordset.md) method to delete records.  <br/> |
|**adFind** <br/> |0x80000  <br/> |Supports the [Find](find-method-ado.md) method to locate a row in a [Recordset](recordset-object-ado.md).  <br/> |
|**adHoldRecords** <br/> |0x100  <br/> |Retrieves more records or changes the next position without committing all pending changes.  <br/> |
|**adIndex** <br/> |0x100000  <br/> |Supports the [Index](index-property-ado.md) property to name an index.  <br/> |
|**adMovePrevious** <br/> |0x200  <br/> |Supports the [MoveFirst](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) and [MovePrevious](movefirst-movelast-movenext-and-moveprevious-methods-ado.md) methods, and [Move](move-method-ado.md) or [GetRows](getrows-method-ado.md) methods to move the current record position backward without requiring bookmarks.  <br/> |
|**adNotify** <br/> |0x40000  <br/> |Indicates that the underlying data provider supports notifications (which determines whether **Recordset** events are supported).  <br/> |
|**adResync** <br/> |0x20000  <br/> |Supports the [Resync](resync-method-ado.md) method to update the cursor with the data that is visible in the underlying database.  <br/> |
|**adSeek** <br/> |0x200000  <br/> |Supports the [Seek](seek-method-ado.md) method to locate a row in a **Recordset**.  <br/> |
|**adUpdate** <br/> |0x1008000  <br/> |Supports the [Update](update-method-ado.md) method to modify existing data.  <br/> |
|**adUpdateBatch** <br/> |0x10000  <br/> |Supports batch updating ([UpdateBatch](updatebatch-method-ado.md) and [CancelBatch](cancelbatch-method-ado.md) methods) to transmit groups of changes to the provider.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.CursorOption.ADDNEW  <br/> |
|AdoEnums.CursorOption.APPROXPOSITION  <br/> |
|AdoEnums.CursorOption.BOOKMARK  <br/> |
|AdoEnums.CursorOption.DELETE  <br/> |
|AdoEnums.CursorOption.FIND  <br/> |
|AdoEnums.CursorOption.HOLDRECORDS  <br/> |
|AdoEnums.CursorOption.INDEX  <br/> |
|AdoEnums.CursorOption.MOVEPREVIOUS  <br/> |
|AdoEnums.CursorOption.NOTIFY  <br/> |
|AdoEnums.CursorOption.RESYNC  <br/> |
|AdoEnums.CursorOption.SEEK  <br/> |
|AdoEnums.CursorOption.UPDATE  <br/> |
|AdoEnums.CursorOption.UPDATEBATCH  <br/> |
   

