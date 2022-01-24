---
title: "Developing Excel Cluster Connectors"
manager: lindalu
ms.date: 1/22/2022
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: b538ae44-37d2-496b-b6e7-b0e39f6e38cb
description: "Learn how to develop Excel cluster connectors"
---

# Developing Excel cluster connectors

**Applies to**: Excel 2013 | Office 2013 | Visual Studio
  
Excel cluster connectors provide a means for automatically offloading cluster-safe user-defined function calls in an XLL to a clustered server. For a description of cluster-safe user-defined functions, see [Cluster Safe Functions](cluster-safe-functions.md). This offloading can improve performance by enabling more computing resources to be used. A cluster connector is typically developed by a high performance compute cluster vendor.
  
## Cluster connectors

A cluster connector is a DLL that provides defined entry points that Excel uses to coordinate cluster-safe user-defined function calls. It serves as an interface between Excel and the high-performance compute cluster, for session management, for making function calls (by passing the fully-qualified function name and the call's actual arguments), and for returning call results to Excel through a callback mechanism.
  
To create a cluster connector, create a DLL that exposes the entry points listed in [Excel Cluster Connector Functions](excel-cluster-connector-functions.md).
  
## Install a cluster connector

To make a cluster connector available in Excel, the setup code of the connector must install the DLL of the connector on the computer where Excel is installed. In addition, the setup code of the connector must add an entry for the connector under the following registry key:
  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\Excel\Excel Cluster Connectors\
  
Add a node to this key for the cluster connector that specifies the following strings:
  
- `Name`—the name that will appear in the list of cluster connectors in Excel.

- `Filename`—the full path for the DLL.
