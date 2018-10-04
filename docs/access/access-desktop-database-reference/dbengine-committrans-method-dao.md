﻿---
title: DBEngine.CommitTrans Method (DAO)
TOCTitle: CommitTrans Method
ms:assetid: 0c9d345f-13ff-7fe6-789d-fbdb43fa54b8
ms:mtpsurl: https://msdn.microsoft.com/library/Ff845171(v=office.15)
ms:contentKeyID: 48543197
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DBEngine.CommitTrans Method (DAO)


**Applies to**: Access 2013 | Office 2013

Ends the current transaction and saves the changes.

## Syntax

*expression* .CommitTrans(***Option***)

*expression* A variable that represents a **DBEngine** object.

### Parameters

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Name</p></th>
<th><p>Required/Optional</p></th>
<th><p>Data Type</p></th>
<th><p>Description</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Option</p></td>
<td><p>Optional</p></td>
<td><p><strong>Long</strong></p></td>
<td><p>In a Microsoft Access workspace, you can include the <strong>dbForceOSFlush</strong> constant with <strong>CommitTrans</strong>. This forces the database engine to immediately flush all updates to disk, instead of caching them temporarily. Without using this option, a user could get control back immediately after the application program calls <strong>CommitTrans</strong>, turn the computer off, and not have the data written to disk. While using this option may affect your application's performance, it is useful in situations where the computer could be shut off before cached updates are saved to disk.</p></td>
</tr>
</tbody>
</table>


## Remarks

The transaction methods **BeginTrans**, **CommitTrans**, and **Rollback** manage transaction processing during a session defined by a **Workspace** object. You use these methods with a **Workspace** object when you want to treat a series of changes made to the databases in a session as one unit.

Typically, you use transactions to maintain the integrity of your data when you must both update records in two or more tables and ensure changes are completed (committed) in all tables or none at all (rolled back). For example, if you transfer money from one account to another, you might subtract an amount from one and add the amount to another. If either update fails, the accounts no longer balance. Use the **BeginTrans** method before updating the first record, and then, if any subsequent update fails, you can use the **Rollback** method to undo all of the updates. Use the **CommitTrans** method after you successfully update the last record.


> [!NOTE]
> <P>Within one <STRONG>Workspace</STRONG> object, transactions are always global to the <STRONG>Workspace</STRONG> and aren't limited to only one <STRONG>Connection</STRONG> or <STRONG>Database</STRONG> object. If you perform operations on more than one connection or database within a <STRONG>Workspace</STRONG> transaction, resolving the transaction (that is, using the <STRONG>CommitTrans</STRONG> or <STRONG>Rollback</STRONG> method) affects all operations on all connections and databases within that workspace.</P>



After you use **CommitTrans**, you can't undo changes made during that transaction unless the transaction is nested within another transaction that is itself rolled back. If you nest transactions, you must resolve the current transaction before you can resolve a transaction at a higher level of nesting.

If you want to have simultaneous transactions with overlapping, non-nested scopes, you can create additional **Workspace** objects to contain the concurrent transactions.

If you close a **Workspace** object without resolving any pending transactions, the transactions are automatically rolled back.

If you use the **CommitTrans** or **Rollback** method without first using the **BeginTrans** method, an error occurs.

Some ISAM databases used in a Microsoft Access workspace may not support transactions, in which case the **Transactions** property of the **Database** object or **Recordset** object is **False**. To make sure the database supports transactions, check the value of the **Transactions** property of the **Database** object before using the **BeginTrans** method. If you are using a **Recordset** object based on more than one database, check the **Transactions** property of the **Recordset** object. If a **Recordset** is based entirely on Microsoft Access database engine tables, you can always use transactions. **Recordset** objects based on tables created by other database products, however, may not support transactions. For example, you can't use transactions in a **Recordset** based on a Paradox table. In this case, the **Transactions** property is **False**. If the **Database** or **Recordset** doesn't support transactions, the methods are ignored and no error occurs.

You can't nest transactions if you are accessing ODBC data sources through the Microsoft Access database engine.

In ODBC workspaces, when you use **CommitTrans** your cursor may no longer be valid. Use the **Requery** method to view the changes in the **Recordset**, or close and re-open the **Recordset**.


> [!NOTE]
> <UL>
> <LI>
> <P>You can often improve the performance of your application by breaking operations that require disk access into transaction blocks. This buffers your operations and may significantly reduce the number of times a disk is accessed.</P>
> <LI>
> <P>In a Microsoft Access workspace, transactions are logged in a file kept in the directory specified by the TEMP environment variable on the workstation. If the transaction log file exhausts the available storage on your TEMP drive, the database engine triggers a run-time error. At this point, if you use <STRONG>CommitTrans</STRONG>, an indeterminate number of operations are committed, but the remaining uncompleted operations are lost, and the operation has to be restarted. Using a <STRONG>Rollback</STRONG> method releases the transaction log and rolls back all operations in the transaction.</P>
> <LI>
> <P>Closing a clone <STRONG>Recordset</STRONG> within a pending transaction will cause an implicit <STRONG>Rollback</STRONG> operation.</P></LI></UL>


