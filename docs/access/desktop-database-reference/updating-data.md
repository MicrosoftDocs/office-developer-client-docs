---
title: Updating Data (Access desktop database reference)
TOCTitle: Updating Data
ms:assetid: 02e82066-77c8-cbb2-db28-98e2fc94404c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248794(v=office.15)
ms:contentKeyID: 48542970
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Updating data


**Applies to**: Access 2013, Office 2013

Update behavior and functionality is largely dependent upon update mode (lock type), cursor type, and cursor location.

Use the **Update** method to save any changes you have made to the current record of a **Recordset** object since calling the **AddNew** method or since changing any field values in an existing record. The **Recordset** object must support updates.

If the **Recordset** object supports batch updating, you can cache multiple changes to one or more records locally until you call the **UpdateBatch** method. If you are editing the current record or adding a new record when you call the **UpdateBatch** method, ADO will automatically call the **Update** method to save any pending changes to the current record before transmitting the batched changes to the provider.

The current record remains current after you call the **Update** or **UpdateBatch** methods.

This section includes the following topics:

- [Immediate mode](immediate-mode.md)
- [Transaction processing](transaction-processing.md)
- [Batch mode (ADO)](batch-mode.md)

