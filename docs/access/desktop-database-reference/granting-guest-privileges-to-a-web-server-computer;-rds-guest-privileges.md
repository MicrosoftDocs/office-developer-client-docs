---
title: Granting guest privileges to a web server computer; RDS guest privileges
TOCTitle: Granting guest privileges to a web server computer; RDS guest privileges
ms:assetid: 4ec9c05b-36f6-de22-b848-0cb8573f9dd1
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249254(v=office.15)
ms:contentKeyID: 48544766
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Granting guest privileges to a web server computer; RDS guest privileges

**Applies to**: Access 2013, Office 2013

The anonymous web server account (IUSR\_*ComputerName*) must be added to the Guests local group on the web server computer to use RDS.

**To grant guest privileges to a web server computer**

1.  On your Microsoft Windows 2000 Server computer, click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Computer Management**.

2.  In the console tree, in **Local Users and Groups**, click **Groups**.

3.  Select the **Guests** local group. From the **Action** menu, choose **Properties**.

4.  In the **Guests Properties** dialog box, click **Add**.

5.  If the anonymous web server account does not appear in the list in the **Select Users or Groups** dialog box, type its name (IUSR\_*ComputerName*) into the bottom blank box, and then click **Add**.

6.  Click **OK**.

