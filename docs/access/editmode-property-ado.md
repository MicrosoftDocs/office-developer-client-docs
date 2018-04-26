---
title: "EditMode Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 28ca8f14-abee-ad20-9c16-11bb36b487e4
---

# EditMode Property (ADO)

Indicates the editing status of the current record.
  
## Return Value

Returns an [EditModeEnum](editmodeenum.md) value. 
  
## Remarks

ADO maintains an editing buffer associated with the current record. This property indicates whether changes have been made to this buffer, or whether a new record has been created. Use the **EditMode** property to determine the editing status of the current record. You can test for pending changes if an editing process has been interrupted and determine whether you need to use the [Update](update-method-ado.md) or [CancelUpdate](cancelupdate-method-ado.md) method. 
  
See the [AddNew](addnew-method-ado.md) method for a more detailed description of the **EditMode** property under different editing conditions. 
  
When a call to [Delete](delete-method-ado-recordset.md) does not successfully delete the record or records in the data source (due to referential integrity violations, for example), the [Recordset](recordset-object-ado.md) will remain in edit mode ( **EditMode** = **adEditInProgress** ). This means that **CancelUpdate** must be called before moving off the current record (with [Move](move-method-ado.md), [NextRecordset](nextrecordset-method-ado.md), or [Close](close-method-ado.md), for example).
  
> [!NOTE]
> **EditMode** can return a valid value only if there is a current record. **EditMode** will return an error if [BOF or EOF](bof-eof-properties-ado.md) is true, or if the current record has been deleted. 
  

