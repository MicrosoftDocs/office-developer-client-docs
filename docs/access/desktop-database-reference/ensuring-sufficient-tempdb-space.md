---
title: Ensuring sufficient TempDB space
TOCTitle: Ensuring sufficient TempDB space
ms:assetid: 2729c118-ec8b-1fcb-4a90-56b57823b24c
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249034(v=office.15)
ms:contentKeyID: 48543830
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Ensuring sufficient TempDB space


**Applies to**: Access 2013, Office 2013

If errors occur while handling [Recordset](recordset-object-ado.md) objects that need processing space on Microsoft SQL Server 6.5, you may need to increase the size of the TempDB. (Some queries require temporary processing space; for example, a query with an ORDER BY clause requires a sort of the **Recordset**, which requires some temporary space.)

> [!IMPORTANT]
> Read through this procedure before performing the actions because it isn't as easy to shrink a device once it is expanded.

> [!NOTE]
> By default in Microsoft SQL Server 7.0 and later, TempDB is set to automatically grow as needed. Therefore, this procedure may only be necessary on servers running versions earlier than 7.0.



**To increase the TempDB space on SQL Server 6.5**

1.  Start Microsoft SQL Server Enterprise Manager, open the tree for the Server, and then open the Database Devices tree.

2.  Select a (physical) device to expand, such as Master, and double-click the device to open the **Edit Database Device** dialog box. This dialog box shows how much space the current databases are using.

3.  In the **Size** box, increase the device to the desired amount (for example, 50 megabytes (MB) of hard disk space).

4.  Click **Change Now** to increase the amount of space to which the (logical) TempDB can expand.

5.  Open the Databases tree on the server, and then double-click **TempDB** to open the **Edit Database** dialog box. The **Database** tab lists the amount of space currently allocated to TempDB (**Data Size**). By default, this is 2 MB.

6.  Under the **Size** group, click **Expand**. The graphs show the available and allocated space on each of the physical devices. The bars in maroon color represent available space.

7.  Select a **Log Device**, such as Master, to display the available size in the **Size (MB)** box.

8.  Click **Expand Now** to allocate that space to the TempDB database. The **Edit Database** dialog box displays the new allocated size for TempDB.

For more information about this topic, search the Microsoft SQL Server Enterprise Manager Help file for "Expand Database dialog box."

