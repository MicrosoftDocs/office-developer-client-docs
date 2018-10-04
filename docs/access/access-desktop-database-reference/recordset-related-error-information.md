---
title: Recordset-Related Error Information
TOCTitle: Recordset-Related Error Information
ms:assetid: 388308c7-e121-bd12-228a-312c897b8c55
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249136(v=office.15)
ms:contentKeyID: 48544222
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Recordset-Related Error Information


_**Applies to:** Access 2013 | Office 2013_

During batch processing, the **Status** property of the **Recordset** object provides information about the individual records in the **Recordset**. Before a batch update takes place, the **Status** property of the **Recordset** reflects information about records to be added, changed and deleted. After **UpdateBatch** has been called, the **Status** property indicates the success or failure of the operation. As you move from record to record in the **Recordset,** the value of the **Status** property changes to describe the status of the current record.

