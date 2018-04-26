---
title: "SkipLine Method (ADO)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 419c24c3-6b84-eed0-5884-f2dcd485dc3d

---

# SkipLine Method (ADO)

Skips one entire line when reading a text stream.
  
## Syntax

 *Stream*  . **SkipLine**
  
## Remarks

All characters up to, and including the next line separator, are skipped. By default, the [LineSeparator](lineseparator-property-ado.md) is **adCRLF**. If you attempt to skip past [EOS](eos-property-ado.md), the current position will simply remain at **EOS**. 
  
The **SkipLine** method is used with text streams ( [Type](type-property-ado-stream.md) is **adTypeText** ). 
  

