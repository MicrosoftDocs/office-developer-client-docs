---
title: Configuring DataFactory for Safe or Unrestricted Modes
TOCTitle: Configuring DataFactory for Safe or Unrestricted Modes
ms:assetid: 1516068f-1b02-3236-f6a9-9fdeff098e52
ms:mtpsurl: https://msdn.microsoft.com/library/JJ248915(v=office.15)
ms:contentKeyID: 48543400
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Configuring DataFactory for Safe or Unrestricted Modes


**Applies to**: Access 2013 | Office 2013

By default, ADO is installed with a "safe" [RDSServer.DataFactory](datafactory-object-rdsserver.md) configuration. Safe mode for RDS Server components means that the following are true:

1.  Handler is required with the RDSServer.DataFactory (this is mandated by a registry key setting).

2.  The default handler, msdfmap.handler, is registered, present in the safe-handler list, and marked as the default handler.

3.  Msdfmap.ini file is installed in the Windows directory. You must configure this file according to your needs, before using RDS in three-tier mode.

Optionally, you can configure an unrestricted **DataFactory** installation. **DataFactory** can be used directly without the custom handler. Users can still use a custom handler by modifying the connection strings, but it is not required. For more information about the implications of using the **RDSServer.DataFactory** object, see [Securing RDS Applications](securing-rds-applications.md).

The registry file handsafe.reg has been provided to set up the handler registry entries for a safe configuration. To run in safe mode, run handsafe.reg. The registry file handunsf.reg has been provided to set up the handler registry entries for an unrestricted configuration. To run in unrestricted mode, run handunsf.reg.

<<<<<<< HEAD
After running either handsafe.reg or handunsf.reg, you must stop and restart the World Wide Web Publishing Service on the Web server by typing the following commands in a command window: "NET STOP W3SVC" and "NET START W3SVC".
=======
After running either handsafe.reg or handunsf.reg, you must stop and restart the World Wide Web Publishing Service on the web server by typing the following commands in a command window: "NET STOP W3SVC" and "NET START W3SVC".
>>>>>>> master

For more information about using the customization handler feature of RDS, see the technical article Using the Customization Handler Feature in RDS 2.1.

