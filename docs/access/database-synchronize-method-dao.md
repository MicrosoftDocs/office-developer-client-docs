---
title: "Database.Synchronize Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1053357
  
localization_priority: Normal
ms.assetid: 5e716a4a-2430-8106-5c34-a02dd28bc4f6
description: "Synchronizes two replicas. (Microsoft Access workspaces only)."
---

# Database.Synchronize Method (DAO)

Synchronizes two replicas. (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **Synchronize**( ** *DbPathName* **, ** *ExchangeType* ** ) 
  
 *expression*  A variable that represents a **Database** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _DbPathName_ <br/> |Required  <br/> |**String** <br/> |The path to the target replica with which database will be synchronized.  <br/> |
| _ExchangeType_ <br/> |Optional  <br/> |**Variant** <br/> |A **[SynchronizeTypeEnum](synchronizetypeenum-enumeration-dao.md)** constant indicating which direction to synchronize changes between the two databases.  <br/> |
   
## Remarks

You use **Synchronize** to exchange data and design changes between two databases. Design changes always happen first. Both databases must be at the same design level before they can exchange data. For example, an exchange of type **dbRepExportChanges** might cause design changes at a replica even though data changes flow only from the  _database_ to  _DbPathName_.
  
The replica identified in  _DbPathName_ must be part of the same replica set. If both replicas have the same **ReplicaID** property setting or are Design Masters for two different replica sets, the synchronization fails. 
  
When you synchronize two replicas over the Internet, you must use the **dbRepSyncInternet** constant. In this case, you specify a Uniform Resource Locator (URL) address for the  _DbPathName_ argument instead of specifying a local area network path. 
  
> [!NOTE]
> You can't synchronize partial replicas with other partial replicas. See the **[PopulatePartial](database-populatepartial-method-dao.md)** method for more information. 
  

