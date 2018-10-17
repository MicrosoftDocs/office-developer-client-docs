---
title: Children Property (ADO MD)
TOCTitle: Children Property (ADO MD)
ms:assetid: 66eff203-68e5-a36d-eb2f-2e9faa80deb6
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249400(v=office.15)
ms:contentKeyID: 48545352
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Children Property (ADO MD)


**Applies to**: Access 2013 | Office 2013

Returns a [Members](members-collection-ado-md.md) collection for which the current [Member](member-object-ado-md.md) is the parent in the hierarchy.

<<<<<<< HEAD
## Return Values
=======
## Return values
>>>>>>> master

Returns a **Members** collection and is read-only.

## Remarks

The **Children** property contains a **Members** collection for which the current **Member** is the hierarchical parent. Leaf level **Member** objects have no child members in the **Members** collection. This property is only supported on **Member** objects belonging to a [Level](level-object-ado-md.md) object. An error occurs when this property is referenced from **Member** objects belonging to a [Position](position-object-ado-md.md) object.

