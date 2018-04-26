---
title: "Recordset.BOF Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: c50a0c5f-1b26-33ea-4cf2-311f9514a94a

description: "Returns a value that indicates whether the current record position is before the first record in a Recordset object. Read-only Boolean ."
---

# Recordset.BOF Property (DAO)

Returns a value that indicates whether the current record position is before the first record in a **Recordset** object. Read-only **Boolean**. 
  
## Syntax

 *expression*  . **BOF**
  
 *expression*  A variable that represents a **Recordset** object. 
  
## Remarks

You can use the **BOF** and **EOF** properties to determine whether a **Recordset** object contains records or whether you've gone beyond the limits of a **Recordset** object when you move from record to record. 
  
The location of the current record pointer determines the **BOF** and **EOF** return values. 
  
If either the **BOF** or **EOF** property is **True**, there is no current record. 
  
If you open a **Recordset** object containing no records, the **BOF** and **EOF** properties are set to **True**, and the **Recordset** object's **RecordCount** property setting is 0. When you open a **Recordset** object that contains at least one record, the first record is the current record and the **BOF** and **EOF** properties are **False**; they remain **False** until you move beyond the beginning or end of the **Recordset** object by using the **MovePrevious** or **MoveNext** method, respectively. When you move beyond the beginning or end of the **Recordset**, there is no current record or no record exists. 
  
If you delete the last remaining record in the **Recordset** object, the **BOF** and **EOF** properties may remain **False** until you attempt to reposition the current record. 
  
If you use the **MoveLast** method on a **Recordset** object containing records, the last record becomes the current record; if you then use the **MoveNext** method, the current record becomes invalid and the **EOF** property is set to **True**. Conversely, if you use the **MoveFirst** method on a **Recordset** object containing records, the first record becomes the current record; if you then use the **MovePrevious** method, there is no current record and the **BOF** property is set to **True**. 
  
Typically, when you work with all the records in a **Recordset** object, your code will loop through the records by using the **MoveNext** method until the **EOF** property is set to **True**. 
  
If you use the **MoveNext** method while the **EOF** property is set to **True** or the **MovePrevious** method while the **BOF** property is set to **True**, an error occurs. 
  
This table shows which Move methods are allowed with different combinations of the **BOF** and **EOF** properties. 
  
||**MoveFirst,          MoveLast**|**MovePrevious,          Move < 0**|**        Move 0**|**MoveNext,          Move > 0**|
|:-----|:-----|:-----|:-----|:-----|
|**BOF=True,**         **EOF=False** <br/> |Allowed  <br/> |Error  <br/> |Error  <br/> |Allowed  <br/> |
|**BOF=False,**         **EOF=True** <br/> |Allowed  <br/> |Allowed  <br/> |Error  <br/> |Error  <br/> |
|Both **True** <br/> |Error  <br/> |Error  <br/> |Error  <br/> |Error  <br/> |
|Both **False** <br/> |Allowed  <br/> |Allowed  <br/> |Allowed  <br/> |Allowed  <br/> |
   
Allowing a Move method doesn't mean that the method will successfully locate a record. It merely indicates that an attempt to perform the specified Move method is allowed and won't generate an error. The state of the **BOF** and **EOF** properties may change as a result of the attempted Move. 
  
An **OpenRecordset** method internally invokes a **MoveFirst** method. Therefore, using an **OpenRecordset** method on an empty set of records sets the **BOF** and **EOF** properties to **True**. (See the following table for the behavior of a failed **MoveFirst** method.) 
  
All Move methods that successfully locate a record will set both **BOF** and **EOF** to **False**. 
  
In a Microsoft Access workspace, if you add a record to an empty **Recordset**, **BOF** will become **False**, but **EOF** will remain **True**, indicating that the current position is at the end of **Recordset**. 
  
Any **Delete** method, even if it removes the only remaining record from a **Recordset**, won't change the setting of the **BOF** or **EOF** property. 
  
The following table shows how Move methods that don't locate a record affect the **BOF** and **EOF** property settings. 
  
||**BOF**|**EOF**|
|:-----|:-----|:-----|
|**MoveFirst**, **MoveLast** <br/> |**True** <br/> |**True** <br/> |
|**Move** 0  <br/> |No change  <br/> |No change  <br/> |
|**MovePrevious**, **Move** < 0  <br/> |**True** <br/> |No change  <br/> |
|**MoveNext**, **Move** > 0  <br/> |No change  <br/> |**True** <br/> |
   

