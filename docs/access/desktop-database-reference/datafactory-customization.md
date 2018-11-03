---
title: DataFactory customization
TOCTitle: DataFactory customization
ms:assetid: 43cd7416-1f05-87ee-22f0-6cf0d2d1b39f
ms:mtpsurl: https://msdn.microsoft.com/library/JJ249205(v=office.15)
ms:contentKeyID: 48544511
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DataFactory customization


**Applies to**: Access 2013, Office 2013

Remote Data Service (RDS) provides a way to easily perform data access in a three-tier client/server system. A client data control specifies connection and command string parameters to perform a query on a remote data source, or connection string and [Recordset](recordset-object-ado.md) object parameters to perform an update.

The parameters are passed to a server program, which performs the data-access operation on the remote data source. RDS provides a default server program called the [RDSServer.DataFactory](datafactory-object-rdsserver.md) object. The **RDSServer.DataFactory** object returns any **Recordset** object produced by a query to the client.

However, the **RDSServer.DataFactory** is limited to performing queries and updates. It cannot perform any validation or processing on the connection or command strings.

With ADO, you can specify that the **DataFactory** work in conjunction with another type of server program called a *handler*. The handler can modify client connection and command strings before they are used to access the data source. In addition, the handler can enforce access rights, which govern the ability of the client to read and write data to the data source.

The parameters the handler uses to modify client parameters and access rights are specified in sections of a customization file.

See the following topics for more information about customizing the **DataFactory** object:

- [Understanding the Customization File](understanding-the-customization-file.md)
- [Customization File Connect section](customization-file-connect-section.md)
- [Customization File SQL section](customization-file-sql-section.md)
- [Customization File UserList section](customization-file-userlist-section.md)
- [Customization File Logs section](customization-file-logs-section.md)
- [Required client settings](https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/required-client-settings)
- [Writing your own customized handler](https://docs.microsoft.com/office/vba/access/concepts/miscellaneous/writing-your-own-customized-handler)
