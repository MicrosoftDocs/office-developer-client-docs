---
title: "SetEOS Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: d438eecf-7ab3-a07d-b6d5-8816db4aae7c

---

# SetEOS Method (ADO)

Sets the position that is the end of the stream.
  
## Syntax

 *Stream*  . **SetEOS**
  
## Remarks

 **SetEOS** updates the value of the [EOS](eos-property-ado.md) property, by making the current [Position](position-property-ado.md) the end of the stream. Any bytes or characters following the current position are truncated. 
  
Since [Write](write-method-ado.md), [WriteText](writetext-method-ado.md), and [CopyTo](copyto-method-ado.md) do not truncate any extra values in existing **Stream** objects, you can truncate these bytes or characters by setting the new end-of-stream position with **SetEOS**. 
  
> [!CAUTION]
> If you set **EOS** to a position before the actual end of the stream, you will lose all data after the new **EOS** position. 
  

