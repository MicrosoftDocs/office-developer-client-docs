---
title: Enabling a DLL to Run on DCOM
TOCTitle: Enabling a DLL to Run on DCOM
ms:assetid: b405f767-91f0-c869-d34e-7a953de49106
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249859(v=office.15)
ms:contentKeyID: 48547211
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Enabling a DLL to Run on DCOM


_**Applies to:** Access 2013 | Office 2013_

The following steps outline how to enable a business object dynamic-link libraries to use both DCOM and Microsoft® Internet Information Services (HTTP) via Component Services.

1.  Create a new empty package in the Component Services MMC snap-in. You will use the Component Services MMC snap-in to create a package and add the DLL into this package. This makes the .dll accessible through DCOM, but it removes the accessibility through IIS. (If you check in the registry for the .dll, the **Inproc** key is now empty; setting the Activation attribute, explained later in this topic, adds a value in the **Inproc** key.)

2.  Install a business object into the package. -or- Import the [RDSServer.DataFactory](datafactory-object-rdsserver.md) object into the package.

3.  Set the Activation attribute for the package to **In the creator's process** (Library application). To make the .dll accessible through DCOM and IIS on the same computer, you must set the component's Activation attribute in the Component Services MMC snap-in. After you set the attribute to **In the creator's process**, you will notice that an **Inproc** server key in the registry has been added that points to a Component Services surrogate .dll.

