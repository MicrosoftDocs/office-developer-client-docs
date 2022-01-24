---
title: "Excel Cluster Connector Functions"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
 
ms.localizationpriority: medium
ms.assetid: 65927ef9-29f7-499a-a1c1-6f672c09bb6b

---

# Excel Cluster Connector Functions

 **Applies to**: Excel 2013 | Office 2013 | Visual Studio 
  
Microsoft Excel 2013 cluster connector DLLs must implement the functions described in this section.
  
The return values mentioned in reference topics in this section are defined in the SDK include file, xlcall.h.
  
## Cluster Connector Architecture

Excel calls entry points in a cluster connector to transfer user-defined function calls to a high-performance compute cluster, and for cluster session management.
  
## In this section

[CallUDF](calludf.md)
  
[CancelOutstandingRequests](canceloutstandingrequests.md)
  
[CloseSession](closesession.md)
  
[OpenSession](opensession.md)
  
[PingSession](pingsession.md)
  
[ShowOptions](showoptions.md)
  
## See also



[Developing Excel Cluster Connectors](developing-excel-cluster-connectors.md)
  
[Cluster Safe Functions](cluster-safe-functions.md)

