---
title: "RDS Object Model Summary"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 0355d62a-dabb-8643-5c43-1e98ccf7f3b0
description: ""
---

# RDS Object Model Summary

|**Object**|**Description**|
|:-----|:-----|
|[RDS.DataSpace](dataspace-object-rds.md) <br/> |This object contains a method to obtain a server proxy. The proxy may be the default or a custom server program (business object). The server program may be invoked on the Internet, an intranet, a local area network, or be a local dynamic-link library.  <br/> |
|[RDSServer.DataFactory](datafactory-object-rdsserver.md) <br/> |This object represents the default server program. It executes the default RDS data retrieval and update behavior.  <br/> |
|[RDS.DataControl](datacontrol-object-rds.md) <br/> |This object can automatically invoke the **RDS.DataSpace** and **RDSServer.DataFactory** objects. Use this object to invoke the default RDS data retrieval or update behavior. This object also provides the means for visual controls to access the returned **Recordset** object.  <br/> |
   

