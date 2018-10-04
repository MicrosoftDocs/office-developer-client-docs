---
title: Recordset.BatchCollisions Property (DAO)
TOCTitle: BatchCollisions Property
ms:assetid: 53e5572b-770c-9ea5-31a5-984abdf66faa
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff194079(v=office.15)
ms:contentKeyID: 48544881
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset.BatchCollisions Property (DAO)


_**Applies to:** Access 2013 | Office 2013_

## Syntax

*expression* .BatchCollisions

*expression* A variable that represents a **Recordset** object.

## Remarks

This property contains an array of bookmarks to rows that encountered a collision during the last attempted batch **[Update](recordset-update-method-dao.md)** call. The **[BatchCollisionCount](recordset-batchcollisioncount-property-dao.md)** property indicates the number of elements in the array.

If you set the working **[Recordset](recordset-object-dao.md)** object's **[Bookmark](recordset-bookmark-property-dao.md)** property to bookmark values in the **BatchCollisions** array, you can move to each record that failed to complete the most recent batch-mode Update operation.

After the collision records are corrected, you can call the batch mode **Update** method again. At this point DAO attempts another batch update, and the **BatchCollisions** property again reflects the set of records that failed the second attempt. Any records that succeeded in the previous attempt are not sent in the current attempt, as they now have a **[RecordStatus](recordset-recordstatus-property-dao.md)** property of dbRecordUnmodified. This process can continue as long as collisions occur, or until you abandon the updates and close the result set.

This array is re-created each time you execute a batch-mode **Update** method.

