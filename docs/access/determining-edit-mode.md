---
title: "Determining Edit Mode"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 45e21fa7-94e8-3449-e062-09cbcf15cba8
description: "ADO maintains an editing buffer associated with the current record. The EditMode property indicates whether changes have been made to this buffer or whether a new record has been created. Use EditMode to determine the editing status of the current record. You can test for pending changes if an editing process has been interrupted and determine whether you need to use the Update or CancelUpdate method."
---

# Determining Edit Mode

ADO maintains an editing buffer associated with the current record. The **EditMode** property indicates whether changes have been made to this buffer or whether a new record has been created. Use **EditMode** to determine the editing status of the current record. You can test for pending changes if an editing process has been interrupted and determine whether you need to use the **Update** or **CancelUpdate** method. 
  
 **EditMode** returns one of the **EditModeEnum** constants, which are listed in the following table. 
  
|**Constant**|**Description**|
|:-----|:-----|
|**adEditNone** <br/> |Indicates that no editing operation is in progress.  <br/> |
|**adEditInProgress** <br/> |Indicates that data in the current record has been modified but not saved.  <br/> |
|**adEditAdd** <br/> |Indicates that the **AddNew** method has been called, and the current record in the copy buffer is a new record that has not been saved to the database.  <br/> |
|**adEditDelete** <br/> |Indicates that the current record has been deleted.  <br/> |
   
 **EditMode** can return a valid value only if there is a current record. **EditMode** will return an error if **BOF** or **EOF** is **True** or if the current record has been deleted. 
  

