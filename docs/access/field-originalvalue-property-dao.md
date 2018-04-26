---
title: "Field.OriginalValue Property (DAO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 69ccec1e-311f-6905-e7bb-ad7fa8277494

---

# Field.OriginalValue Property (DAO)

## Syntax

 *expression*  . **OriginalValue**
  
 *expression*  A variable that represents a **Field** object. 
  
## Remarks

During an optimistic batch update, a collision may occur where a second client modifies the same field and record in between the time the first client retrieves the data and the first client's update attempt. The **OriginalValue** property contains the value of the field at the time the last batch **Update** began. If this value does not match the value actually in the database when the batch **Update** attempts to write to the database, a collision occurs. When this happens, the new value in the database will be accessible through the **[VisibleValue](field-visiblevalue-property-dao.md)** property. 
  

