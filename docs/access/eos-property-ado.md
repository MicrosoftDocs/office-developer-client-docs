---
title: "EOS Property (ADO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 97cd23ef-cca8-4dcc-2641-082a0e1b853c
---

# EOS Property (ADO)

Indicates whether the current position is at the end of the stream.
  
## Return Values

Returns a **Boolean** value that indicates whether the current position is at the end of the stream. **EOS** returns **True** if there are no more bytes in the stream; it returns **False** if there are more bytes following the current position. 
  
To set the end of stream position, use the [SetEOS](seteos-method-ado.md) method. To determine the current position, use the [Position](position-property-ado.md) property. 
  

