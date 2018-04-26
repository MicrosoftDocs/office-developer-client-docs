---
title: "FieldEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: fbd415c0-d6b4-278f-318b-98432c013634

---

# FieldEnum

Specifies the special fields referenced in a [Record](record-object-ado.md) object's [Fields](fields-collection-ado.md) collection. 
  
 **Remarks**
  
These constants provide a "shortcut" to accessing special fields associated with a **Record**. Retrieve the [Field](field-object-ado.md) object from the **Fields** collection, and then obtain its contents with the **Field** object's [Value](value-property-ado.md) property. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adDefaultStream** <br/> |-1  <br/> |References the field containing the default [Stream](stream-object-ado.md) object associated with a **Record**.  <br/> |
|**adRecordURL** <br/> |-2  <br/> |References the field containing the absolute URL string for the current **Record**.  <br/> |
   

