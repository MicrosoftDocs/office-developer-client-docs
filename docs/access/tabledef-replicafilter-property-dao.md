---
title: "TableDef.ReplicaFilter Property (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- dao360.chm1055548
  
localization_priority: Normal
ms.assetid: f44273de-2b6a-750f-cb7c-12c3ac2da503
description: "Sets or returns a value on a TableDef object within a partial replica that indicates which subset of records is replicated to that table from a full replica. (Microsoft Access workspaces only)."
---

# TableDef.ReplicaFilter Property (DAO)

Sets or returns a value on a **[TableDef](tabledef-object-dao.md)** object within a partial replica that indicates which subset of records is replicated to that table from a full replica. (Microsoft Access workspaces only). 
  
## Syntax

 *expression*  . **ReplicaFilter**
  
 *expression*  A variable that represents a **TableDef** object. 
  
## Remarks

The setting or return value is a **String** or **Boolean** that indicates which subset of records is replicated, as specified in the following table: 
  
|**Value**|**Description**|
|:-----|:-----|
|A string  <br/> |A criteria that a record in the partial replica table must satisfy in order to be replicated from the full replica.  <br/> |
|**True** <br/> |Replicates all records.  <br/> |
|**False** <br/> |(Default) Doesn't replicate any records.  <br/> |
   
This property is similar to an SQL WHERE clause (without the word WHERE), but you cannot specify subqueries, aggregate functions (such as **Count** ), or user-defined functions within the criteria. 
  
You can only synchronize data between a full replica and a partial replica. You can't synchronize data between two partial replicas. Also, with partial replication you can set restrictions on which records are replicated, but you can't indicate which fields are replicated.
  
Usually, you reset a replica filter when you want to replicate a different set of records. For example, when a sales representative temporarily takes over another sales representative's region, the database application can temporarily replicate data for both regions and then return to the previous filter. In this scenario, the application resets the **ReplicaFilter** property and then repopulates the partial replica. 
  
If your application changes replica filters, you should follow these steps:
  
1. Use the **[Synchronize](database-synchronize-method-dao.md)** method to synchronize your full replica with the partial replica in which the filters are being changed. 
    
2. Use the **ReplicaFilter** property to make the desired changes to the replica filter. 
    
3. Use the **[PopulatePartial](database-populatepartial-method-dao.md)** method to remove all records from the partial replica and transfer all records from the full replica that meet the new replica filter criteria. 
    
To remove a filter, set the **ReplicaFilter** property to **False**. If you remove all filters and invoke the **PopulatePartial** method, no records will appear in any replicated tables in the partial replica. 
  
> [!NOTE]
> If a replica filter has changed, and the **Synchronize** method is invoked without first invoking **PopulatePartial**, a trappable error occurs. 
  
## Example

The following example uses the **ReplicaFilter** property to replicate only customer records from the California region. 
  
```
Sub ReplicaFilterX() 
 
 ' This example assumes the current open database 
 ' is the replica. 
 Dim tdfCustomers As TableDef 
 Dim strFilter As String 
 Dim dbsTemp As Database 
 
 Set dbsTemp = OpenDatabase("Northwind.mdb") 
 Set tdfCustomers = dbsTemp.TableDefs("Customers") 
 
 ' Synchronize with full replica 
 ' before setting replica filter. 
 dbsTemp.Synchronize "C:\SALES\FY96.MDB" 
 
 strFilter = "Region = 'CA'" 
 tdfCustomers.ReplicaFilter = strFilter 
 dbsTemp.PopulatePartial "C:\SALES\FY96.MDB" 
 
 ' Now remove the replica filter (for example purposes 
 ' only). 
 tdfCustomers.ReplicaFilter = False 
 ' Repopulate the database. 
 dbsTemp.PopulatePartial "C:\SALES\DATA96.MDB" 
 
End Sub 
 
```


