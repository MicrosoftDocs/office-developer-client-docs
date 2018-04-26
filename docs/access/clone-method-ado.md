---
title: "Clone Method (ADO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: ca9b2b76-90bf-9a60-2611-3cb4977d5591
---

# Clone Method (ADO)

Creates a duplicate [Recordset](recordset-object-ado.md) object from an existing **Recordset** object. Optionally, specifies that the clone be read-only. 
  
## Syntax

 **Set** *rstDuplicate*  =  *rstOriginal*  . **Clone** (  *LockType*  ) 
  
## Return Value

Returns a **Recordset** object reference. 
  
## Parameters

-  *rstDuplicate* 
    
- An object variable that identifies the duplicate **Recordset** object to be created. 
    
-  *rstOriginal* 
    
- An object variable that identifies the **Recordset** object to be duplicated. 
    
-  *LockType* 
    
- Optional. A [LockTypeEnum](locktypeenum.md) value that specifies either the lock type of the original **Recordset**, or a read-only **Recordset**. Valid values are **adLockUnspecified** or **adLockReadOnly**. 
    
## Remarks

Use the **Clone** method to create multiple, duplicate **Recordset** objects, particularly if you want to maintain more than one current record in a given set of records. Using the **Clone** method is more efficient than creating and opening a new **Recordset** object with the same definition as the original. 
  
The [Filter](filter-property-ado.md) property of the original **Recordset**, if any, will not be applied to the clone. Set the **Filter** property of the new **Recordset** in order to filter the results. The simplest way to copy any existing **Filter** value is to assign it directly, like this: 
  
The current record of a newly created clone is set to the first record.
  
Changes you make to one **Recordset** object are visible in all of its clones regardless of cursor type. However, after you execute [Requery](requery-method-ado.md) on the original **Recordset**, the clones will no longer be synchronized to the original. 
  
Closing the original **Recordset** does not close its copies, nor does closing a copy close the original or any of the other copies. 
  
You can only clone a **Recordset** object that supports bookmarks. Bookmark values are interchangeable; that is, a bookmark reference from one **Recordset** object refers to the same record in any of its clones. 
  
Some **Recordset** events that are triggered will also fire in all **Recordset** clones. However, because the current record can differ between cloned **Recordsets**, the events may not be valid for the clone. 
  
For example, if you change a value of a field, a [WillChangeField](willchangefield-and-fieldchangecomplete-events-ado.md) event will occur in the changed **Recordset** and in all clones. The  *Fields*  parameter of the **WillChangeField** event of a cloned **Recordset** (where the change was not made) will simply refer to the fields of the current record of the clone, which may be a different record than the current record of the original **Recordset** where the change occurred. 
  
The following table provided a full listing of all **Recordset** events and indicates whether they are valid and triggered for any recordset clones generated using the **Clone** method. 
  
|**Event**|**Triggered in clones?**|
|:-----|:-----|
|[EndOfRecordset](endofrecordset-event-ado.md) <br/> |No  <br/> |
|[FetchComplete](fetchcomplete-event-ado.md) <br/> |No  <br/> |
|[FetchProgress](fetchprogress-event-ado.md) <br/> |No  <br/> |
|[FieldChangeComplete](willchangefield-and-fieldchangecomplete-events-ado.md) <br/> |Yes  <br/> |
|[MoveComplete](willmove-and-movecomplete-events-ado.md) <br/> |No  <br/> |
|[RecordChangeComplete](willchangerecord-and-recordchangecomplete-events-ado.md) <br/> |Yes  <br/> |
|[RecordsetChangeComplete](willchangerecordset-and-recordsetchangecomplete-events-ado.md) <br/> |No  <br/> |
|[WillChangeField](willchangefield-and-fieldchangecomplete-events-ado.md) <br/> |Yes  <br/> |
|[WillChangeRecord](willchangerecord-and-recordchangecomplete-events-ado.md) <br/> |Yes  <br/> |
|[WillChangeRecordset](willchangerecordset-and-recordsetchangecomplete-events-ado.md) <br/> |No  <br/> |
|[WillMove](willmove-and-movecomplete-events-ado.md) <br/> |No  <br/> |
   

