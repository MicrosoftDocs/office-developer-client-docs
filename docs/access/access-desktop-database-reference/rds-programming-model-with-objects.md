---
title: RDS Programming Model with Objects
TOCTitle: RDS Programming Model with Objects
ms:assetid: 207150ec-8eb5-bec5-3059-db37a0e28c19
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248987(v=office.15)
ms:contentKeyID: 48543663
ms.date: 09/18/2015
mtps_version: v=office.15
---

# RDS Programming Model with Objects


_**Applies to:** Access 2013 | Office 2013_

The goal of RDS is to gain access to and update data sources through an intermediary such as IIS. The programming model specifies the sequence of activities necessary to accomplish this goal. The object model specifies the objects whose methods and properties affect the programming model.

RDS provides the means to perform the following sequence of actions:

  - Specify the program to be invoked on the server, and obtain a way (proxy) to refer to it from the client ([RDS.DataSpace](dataspace-object-rds.md)).

  - Invoke the server program. Pass parameters to the server program that identifies the data source and the command to issue (proxy or [RDS.DataControl](datacontrol-object-rds.md)).

  - The server program obtains a [Recordset](recordset-object-ado.md) object from the data source, typically by using ADO. Optionally, the **Recordset** object is processed on the server ([RDSServer.DataFactory](datafactory-object-rdsserver.md)).

  - The server program returns the final **Recordset** object to the client application (proxy).

  - On the client, the **Recordset** object is put into a form that can be easily used by visual controls (visual control and **RDS.DataControl**).

  - Changes to the **Recordset** object are sent back to the server and used to update the data source (**RDS.DataControl** or **RDSServer.DataFactory**).

