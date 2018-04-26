---
title: "Database.ReplicaID Property (DAO)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
f1_keywords:
- dao360.chm1053375
  
localization_priority: Normal
ms.assetid: cf2ca8a1-d13f-30e0-2ca1-dd32ac736c56
description: "Returns a 16-byte value that uniquely identifies a database replica (Microsoft Access workspaces only)."
---

# Database.ReplicaID Property (DAO)

Returns a 16-byte value that uniquely identifies a database replica (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **ReplicaID**
  
 *expression*  A variable that represents a **Database** object. 
  
## Remarks

The return value is a **GUID** value that uniquely identifies the replica or Design Master. 
  
The Microsoft Access database engine automatically generates this value when you create a new replica.
  
The **ReplicaID** property of each replica (and the Design Master) is stored in the MSysReplicas system table. 
  
## Example

This example makes a replica from the Design Master of Northwind.mdb, and then returns the replica's **ReplicaID**, which is automatically created by the Microsoft Access database engine. (If you have not yet created a Design Master of Northwind, refer to the **Replicable** property, or change the name of the database in the code to an existing Design Master.) 
  
```
Sub MakeReplicaReplicaIDX() 
 
 Dim dbsNorthwind As Database 
 Dim prpReplicaID As Property 
 Dim dbsReplica As Database 
 
 Set dbsNorthwind = OpenDatabase("Northwind.mdb") 
 
 ' Makes a new replica. 
 dbsNorthwind.MakeReplica "Nwreplica2.mdb", _ 
 "second replica" 
 dbsNorthwind.Close 
 
 ' Opens the new replica to read its ReplicaID. 
 Set dbsReplica = OpenDatabase("Nwreplica2.mdb") 
 
 Debug.Print dbsReplica.ReplicaID 
 dbsReplica.Close 
 
End Sub 
 
```


