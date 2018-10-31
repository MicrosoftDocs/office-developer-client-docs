---
title: TRANSACTION statement (Microsoft Access SQL)
TOCTitle: TRANSACTION statement (Microsoft Access SQL)
ms:assetid: 481e807d-94e4-f201-adac-d25ee89d9220
ms:mtpsurl: https://msdn.microsoft.com/library/Ff193241(v=office.15)
ms:contentKeyID: 48544614
ms.date: 10/18/2018
mtps_version: v=office.15
f1_keywords:
- jetsql40.chm5277472
f1_categories:
- Office.Version=v15
---

# TRANSACTION statement (Microsoft Access SQL)

**Applies to**: Access 2013, Office 2013

Used to initiate and conclude explicit transactions.

## Syntax

**Initiate a new transaction**:

BEGIN TRANSACTION

**Conclude a transaction by committing all work performed during the transaction**:

COMMIT \[TRANSACTION | WORK\]

**Conclude a transaction by rolling back all work performed during the transaction**:

ROLLBACK \[TRANSACTION | WORK\]

## Remarks

Transactions are not started automatically. To start a transaction, you must do so explicitly using BEGIN TRANSACTION.

Transactions can be nested up to five levels deep. To start a nested transaction, use BEGIN TRANSACTION within the context of an existing transaction.

Transactions are not supported for linked tables.

