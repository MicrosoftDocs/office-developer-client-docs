﻿---
title: Using RDS with ODBC Connection Pooling
TOCTitle: Using RDS with ODBC Connection Pooling
ms:assetid: 6e8b023a-d211-44cb-10af-d43174a5d4bc
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249437(v=office.15)
ms:contentKeyID: 48545513
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Using RDS with ODBC Connection Pooling


**Applies to**: Access 2013 | Office 2013

If you're using an ODBC data source, you can use the connection pooling option in Internet Information Services (IIS) to achieve high performance handling of client load. Connection pooling is a resource manager for connections, maintaining the open state on frequently used connections.

To enable connection pooling, refer to the Internet Information Services documentation.

Please note that enabling connection pooling may subject the Web server to other restrictions, as noted in the Microsoft Internet Information Services documentation.

To ensure that connection pooling is stable and provides additional performance gains, you must configure Microsoft SQL Server to use the TCP/IP Socket network library.

To do this, you need to:

  - Configure the SQL Server computer to use TCP/IP Sockets.

  - Configure the Web server to use TCP/IP Sockets.

## Configuring the SQL Server Computer to Use TCP/IP Sockets

On the SQL Server computer, run the SQL Server Setup program so that interactions with the data source use the TCP/IP Socket network library.

**To specify the TCP/IP Socket network library on the SQL Server computer**

**In Microsoft SQL Server 6.5:**

1.  From the **Start** menu, point to **Programs**, point to **Microsoft SQL Server 6.5**, and then click **SQL Setup**.

2.  Click **Continue** twice.

3.  In the **Microsoft SQL Server — Options** dialog box, select **Change Network Support**, and then click **Continue**.

4.  Make sure the **TCP/IP Sockets** check box is selected, and click **OK**.

5.  Click **Continue** to finish, and exit setup.

**In Microsoft SQL Server 7.0:**

1.  From the **Start** menu, point to **Programs**, point to **Microsoft SQL Server 7.0**, and then click **Server Network Utility**.

2.  On the **General** tab of the dialog box, click **Add**.

3.  In the **Add Network Library Configuration** dialog box, click **TCP/IP**.

4.  In the **Port number** and **Proxy address** boxes, enter the port number and proxy address provided by your network administrator.

5.  Click **OK** to finish, and exit setup.

## Configuring the Web Server to Use TCP/IP Sockets

There are two options for configuring the Web server to use TCP/IP Sockets. What you do depends on whether all SQL Servers are accessed from the Web server, or only a specific SQL Server is accessed from the Web server.

If all SQL Servers are accessed from the Web server, you need to run the SQL Server Client Configuration Utility on the Web server computer. The following steps change the default network library for all SQL Server connections made from this IIS Web server to use the TCP/IP Sockets network library.

**To configure the Web server (all SQL Servers)**

**For Microsoft SQL Server 6.5:**

1.  From the **Start** menu, point to **Programs**, point to **Microsoft SQL Server 6.5**, and then click **SQL Client Configuration Utility**.

2.  Click the **Net Library** tab.

3.  In the **Default Network** box, select **TCP/IP Sockets**.

4.  Click **Done** to save changes and exit the utility.

**For Microsoft SQL Server 7.0:**

1.  From the **Start** menu, point to **Programs**, point to **Microsoft SQL Server 7.0**, and then click **Client Network Utility**.

2.  Click the **General** tab.

3.  In the **Default network library** box, click **TCP/IP**.

4.  Click **OK** to save changes and exit the utility.

If a specific SQL Server is accessed from a Web server, you need to run the SQL Server Client Configuration Utility on the Web server computer. To change the network library for a specific SQL Server connection, configure the SQL Server Client software on the Web server computer as follows.

**To configure the Web server (a specific SQL Server)**

**For Microsoft SQL Server 6.5:**

1.  From the **Start** menu, point to **Programs**, point to **Microsoft SQL Server 6.5**, and then click **SQL Client Configuration Utility**.

2.  Click the **Advanced** tab.

3.  In the **Server** box, type the name of the server to connect to using **TCP/IP Sockets**.

4.  In the **DLL Name** box, select **TCP/IP Sockets**.

5.  Click **Add/Modify**. All data sources pointing to this server will now use TCP/IP Sockets.

6.  Click **Done**.

**For Microsoft SQL Server 7.0:**

1.  From the **Start** menu, point to **Programs**, point to **Microsoft SQL Server 7.0**, and then click **Client Configuration Utility**.

2.  Click the **General** tab.

3.  Click **Add**.

4.  Enter the alias of the server in the **Server alias** box. In the **Network libraries** box, click **TCP/IP**. In the **Computer name** box, enter the computer name of the computer that listens for TCP/IP Sockets clients. In the **Port number** box, enter the port on which the SQL Server listens.

5.  Click **OK**, and then **OK** again to exit the utility.

