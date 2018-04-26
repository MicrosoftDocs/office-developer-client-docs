---
title: "RecordCreateOptionsEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 153dc8ff-680c-1482-d386-4c4b33ffc589

---

# RecordCreateOptionsEnum

Specifies whether an existing **Record** should be opened or a new **Record** created for the [Record](record-object-ado.md) object [Open](open-method-ado-record.md) method. The values can be combined with an AND operator. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adCreateCollection** <br/> |0x2000  <br/> |Creates a new **Record** at the node specified by  *Source*  parameter, instead of opening an existing **Record**. If the source points to an existing node, then a run-time error occurs, unless **adCreateCollection** is combined with **adOpenIfExists** or **adCreateOverwrite**.  <br/> |
|**adCreateNonCollection** <br/> |0  <br/> |Creates a new **Record** of type [adSimpleRecord](recordtypeenum.md).  <br/> |
|**adCreateOverwrite** <br/> |0x4000000  <br/> |Modifies the creation flags **adCreateCollection**, **adCreateNonCollection**, and **adCreateStructDoc**. When OR is used with this value and one of the creation flag values, if the source URL points to an existing node or **Record**, then the existing **Record** is overwritten and a new one is created in its place. This value cannot be used together with **adOpenIfExists**.  <br/> |
|**adCreateStructDoc** <br/> |0x80000000  <br/> |Creates a new **Record** of type [adStructDoc](recordtypeenum.md), instead of opening an existing **Record**.  <br/> |
|**adFailIfNotExists** <br/> |-1  <br/> |Default. Results in a run-time error if  *Source*  points to a non-existent node.  <br/> |
|**adOpenIfExists** <br/> |0x2000000  <br/> |Modifies the creation flags **adCreateCollection**, **adCreateNonCollection**, and **adCreateStructDoc**. When OR is used with this value and one of the creation flag values, if the source URL points to an existing node or **Record** object, then the provider must open the existing **Record** instead of creating a new one. This value cannot be used together with **adCreateOverwrite**.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

