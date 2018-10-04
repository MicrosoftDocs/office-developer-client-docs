---
title: DataFactory Object (RDSServer)
TOCTitle: DataFactory Object (RDSServer)
ms:assetid: 1de76cdd-34dc-8547-29aa-48ad6067bdea
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ248971(v=office.15)
ms:contentKeyID: 48543605
ms.date: 09/18/2015
mtps_version: v=office.15
---

# DataFactory Object (RDSServer)


_**Applies to:** Access 2013 | Office 2013_

This default server-side business object implements methods that provide read/write data access to specified data sources for client-side applications.

## Remarks

The **RDSServer.DataFactory** object is designed as a server-side Automation object that receives client requests. In an Internet implementation, it resides on a Web server and is instantiated by the ADISAPI component. The **RDSServer.DataFactory** object provides read and write access to specified data sources, but doesn't contain any validation or business rules logic.

If you use a method that is available in both the **RDSServer.DataFactory** and [RDS.DataControl](datacontrol-object-rds.md) objects, Remote Data Service uses the **RDS.DataControl** version by default. The default assumes a basic programming scenario, where the **RDSServer.DataFactory** serves as a generic server-side business object.

If you want your Web application to handle task-specific server-side processing, you can replace the **RDSServer.DataFactory** with a custom business object.

You can create server-side business objects that call the **RDSServer.DataFactory** methods, such as [Query](query-method-rds.md) and [CreateRecordset](createrecordset-method-rds.md). This is helpful if you want to add functionality to your business objects, but take advantage of existing Remote Data Service technologies.

The class ID for the **RDSServer.DataFactory** object is 9381D8F5-0288-11D0-9501-00AA00B911A5.

