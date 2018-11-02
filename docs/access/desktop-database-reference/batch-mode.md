---
title: Batch mode (Access desktop database reference)
TOCTitle: Batch mode
ms:assetid: b73921f6-5a12-9b26-ea65-99b32dd763f6
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249883(v=office.15)
ms:contentKeyID: 48547294
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Batch mode

**Applies to**: Access 2013, Office 2013

Batch mode is in effect when the **LockType** property is set to **adLockBatchOptimistic** and batch updating is supported by the provider. Certain lock type settings are not available depending on cursor location. For instance, a pessimistic lock type is not available when the **CursorLocation** is set to **adUseClient**. Conversely, a provider may not support a batch optimistic lock when the cursor location is on the server. You should use batch updating with either a keyset or static cursor only.

The **UpdateBatch** method is used to send **Recordset** changes held in the copy buffer to the server to update the data source. In the following section, we will open a **Recordset** in batch mode, make changes to the copy buffer, and then send our changes to the data source using a call to **UpdateBatch**.

This section includes the following topics:

- [Sending the updates: UpdateBatch](sending-the-updates-updatebatch.md)
- [Filtering for updated records](filtering-for-updated-records.md)
- [Dealing with failed updates](dealing-with-failed-updates.md)
- [Detecting and resolving conflicts](detecting-and-resolving-conflicts.md)
- [Disconnecting and reconnecting the Recordset](disconnecting-and-reconnecting-the-recordset.md)
- [Updating JOINed results: Unique Table](updating-joined-results-unique-table.md)

