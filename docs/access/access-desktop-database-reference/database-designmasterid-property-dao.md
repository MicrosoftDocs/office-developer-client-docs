﻿---
title: Database.DesignMasterID Property (DAO)
TOCTitle: DesignMasterID Property
ms:assetid: c0545561-d44f-5479-8ae0-e3955db91761
ms:mtpsurl: https://msdn.microsoft.com/library/Ff822824(v=office.15)
ms:contentKeyID: 48547508
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- dao360.chm1053417
f1_categories:
- Office.Version=v15
---

# Database.DesignMasterID Property (DAO)


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Remarks  
Example  

Sets or returns a 16-byte value that uniquely identifies the Design Master in a replica set (Microsoft Access workspaces only).

## Syntax

*expression* .DesignMasterID

*expression* A variable that represents a **Database** object.

## Remarks

You should set the **DesignMasterID** property only if you need to move the current Design Master. Setting this property makes a specific replica in the replica set the Design Master.


> [!NOTE]
> <P>Never create a second Design Master in a replica set. The existence of a second Design Master can result in the loss of data.</P>



Under extreme circumstances— for example, if the Design Master is erased or corrupted— you can set this property at the current replica. However, setting this property at a replica when there is already another Design Master in the set might partition your replica set into two irreconcilable sets and prevent any further synchronization of data.

If you decide to make a replica the new Design Master for the set, synchronize it with all the replicas in the replica set before setting the **DesignMasterID** property in the replica. The replica must be open in exclusive mode in order to make it the Design Master.

If you make a replica that is designated read-only into the Design Master, the target replica is made read/write; the old Design Master also remains read/write.

The **DesignMasterID** property setting is stored in the MSysRepInfo system table.

## Example

This example sets the **DesignMasterID** property to the **ReplicaID** property setting of another database, making that database the Design Master in the replica set. The old and new Design Masters are synchronized to update the design change. For this code to work, you must create a Design Master and replica, include their names and paths as appropriate, and run this code from a database other than the old or new Design Master.

``` 
Sub SetNewDesignMaster(strOldDM as String, _ 
 strNewDM as String) 
 
 Dim dbsOld As Database 
 Dim dbsNew As Database 
 
 ' Open the current Design Master in exclusive mode. 
 Set dbsOld = OpenDatabase(strOldDM, True) 
 
 ' Open the database that will become the new 
 ' Design Master. 
 Set dbsNew = OpenDatabase(strNewDM) 
 
 ' Make the new database the Design Master. 
 dbsOld.DesignMasterID = dbsNew.ReplicaID 
 
 ' Synchronize the old Design Master with the new 
 ' Design Master, and allow two-way exchanges. 
 dbsOld.Synchronize strNewDM, dbRepImpExpChanges 
 dbsOld.Close 
 dbsNew.Close 
 
End Sub 
 
```

