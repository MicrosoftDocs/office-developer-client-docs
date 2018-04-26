---
title: "EditModeEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 4da0e504-aca2-b769-04a2-0df687fa4422
---

# EditModeEnum

Specifies the editing status of a record.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adEditNone** <br/> |0  <br/> |Indicates that no editing operation is in progress.  <br/> |
|**adEditInProgress** <br/> |1  <br/> |Indicates that data in the current record has been modified but not saved.  <br/> |
|**adEditAdd** <br/> |2  <br/> |Indicates that the [AddNew](addnew-method-ado.md) method has been called, and the current record in the copy buffer is a new record that has not been saved in the database.  <br/> |
|**adEditDelete** <br/> |4  <br/> |Indicates that the current record has been deleted.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.EditMode.NONE  <br/> |
|AdoEnums.EditMode.INPROGRESS  <br/> |
|AdoEnums.EditMode.ADD  <br/> |
|AdoEnums.EditMode.DELETE  <br/> |
   

