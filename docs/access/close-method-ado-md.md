---
title: "Close Method (ADO MD)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 683788b0-0a96-a165-6b49-8d7036850756
---

# Close Method (ADO MD)

Closes an open cellset.
  
## Syntax

 *Cellset*  . **Close**
  
## Remarks

Using the **Close** method to close a [Cellset](cellset-object-ado-md.md) object will release the associated data, including data in any related [Cell](cell-object-ado-md.md), [Axis](axis-object-ado-md.md), [Position](position-object-ado-md.md), or [Member](member-object-ado-md.md) objects. Closing a **Cellset** does not remove it from memory; you can change its property settings and open it again later. To completely eliminate an object from memory, set the object variable to **Nothing**. 
  
You can later call the [Open](open-method-ado-md.md) method to reopen the **Cellset** using the same or another source string. While the **Cellset** object is closed, retrieving any properties or calling any methods that reference the underlying data or metadata generates an error. 
  

