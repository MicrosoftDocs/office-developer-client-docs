---
title: "SetField Macro Action"
 
 
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 66bd26e3-e8c3-b9a1-2f16-f29adc44a345
description: "The SetField action can be used to assign a value to a field."
---

# SetField Macro Action

The **SetField** action can be used to assign a value to a field. 
  
> [!NOTE]
> The **SetField** action is available only in Data Macros. 
  
## Setting

The **SetField** action has the arguments listed in the following table. 
  
|**Argument**|**Description**|
|:-----|:-----|
|**Name** <br/> |A string that identifies the field.  <br/> |
|**Value** <br/> |An expression that specifies the value to assign to the field.  <br/> |
   
## Remarks

The **SetField** action cannot be used outside of an **[CreateRecord](createrecord-data-block.md)** or **[EditRecord](editrecord-data-block.md)** data block. 
  

