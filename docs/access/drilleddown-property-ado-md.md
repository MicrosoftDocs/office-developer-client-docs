---
title: "DrilledDown Property (ADO MD)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 1dfe728f-8da2-1d2b-7361-8689a0b088b4
---

# DrilledDown Property (ADO MD)

Indicates whether no children immediately follow the member on the axis.
  
## Return Values

Returns a **Boolean** value and is read-only. **DrilledDown** returns **True** if there are no child members of the current member on the axis. **DrilledDown** returns **False** if there is one or more child members of the current member on the axis. 
  
## Remarks

Use the **DrilledDown** property to determine whether there is at least one child of this member on the axis immediately following this member. This information is useful when displaying the member. 
  
This property is only supported on [Member](member-object-ado-md.md) objects belonging to a [Position](position-object-ado-md.md) object. An error occurs when this property is referenced from **Member** objects belonging to a [Level](level-object-ado-md.md) object. 
  

