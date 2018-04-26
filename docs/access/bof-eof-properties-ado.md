---
title: "BOF, EOF Properties (ADO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: f797e140-5572-1a4d-9afc-285f6a3868a8
---

# BOF, EOF Properties (ADO)

- **BOF** — Indicates that the current record position is before the first record in a [Recordset](recordset-object-ado.md) object. 
    
- **EOF** — Indicates that the current record position is after the last record in a **Recordset** object. 
    
## Return Value

The **BOF** and **EOF** properties return **Boolean** values. 
  
## Remarks

Use the **BOF** and **EOF** properties to determine whether a **Recordset** object contains records or whether you've gone beyond the limits of a **Recordset** object when you move from record to record. 
  
The **BOF** property returns **True** (-1) if the current record position is before the first record and **False** (0) if the current record position is on or after the first record. 
  
The **EOF** property returns **True** if the current record position is after the last record and **False** if the current record position is on or before the last record. 
  
If either the **BOF** or **EOF** property is **True**, there is no current record. 
  
If you open a **Recordset** object containing no records, the **BOF** and **EOF** properties are set to **True** (see the [RecordCount](recordcount-property-ado.md) property for more information about this state of a **Recordset** ). When you open a **Recordset** object that contains at least one record, the first record is the current record and the **BOF** and **EOF** properties are **False**. 
  
If you delete the last remaining record in the **Recordset** object, the **BOF** and **EOF** properties may remain **False** until you attempt to reposition the current record. 
  
This table shows which **Move** methods are allowed with different combinations of the **BOF** and **EOF** properties. 
  
||**MoveFirst,          MoveLast**|**MovePrevious,          Move < 0**|**        Move 0**|**MoveNext,          Move > 0**|
|:-----|:-----|:-----|:-----|:-----|
|**BOF=True,**         **EOF=False** <br/> |Allowed  <br/> |Error  <br/> |Error  <br/> |Allowed  <br/> |
|**BOF=False,**         **EOF=True** <br/> |Allowed  <br/> |Allowed  <br/> |Error  <br/> |Error  <br/> |
|Both **True** <br/> |Error  <br/> |Error  <br/> |Error  <br/> |Error  <br/> |
|Both **False** <br/> |Allowed  <br/> |Allowed  <br/> |Allowed  <br/> |Allowed  <br/> |
   
Allowing a **Move** method doesn't guarantee that the method will successfully locate a record; it only means that calling the specified **Move** method won't generate an error. 
  
The following table shows what happens to the **BOF** and **EOF** property settings when you call various **Move** methods but are unable to successfully locate a record. 
  
||**BOF**|**EOF**|
|:-----|:-----|:-----|
|**MoveFirst**, **MoveLast** <br/> |Set to **True** <br/> |Set to **True** <br/> |
|**Move** 0  <br/> |No change  <br/> |No change  <br/> |
|**MovePrevious**, **Move** < 0  <br/> |Set to **True** <br/> |No change  <br/> |
|**MoveNext**, **Move** > 0  <br/> |No change  <br/> |Set to **True** <br/> |
   

