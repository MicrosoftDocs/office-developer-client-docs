---
title: "Database.MakeReplica Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1053371
  
localization_priority: Normal
ms.assetid: b6bf4982-0804-12ce-849f-d2b4ac2e48a5
description: "Makes a new replica from another database replica (Microsoft Access workspaces only)."
---

# Database.MakeReplica Method (DAO)

Makes a new replica from another database replica (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **MakeReplica**( ** *PathName* **, ** *Description* **, ** *Options* ** ) 
  
 *expression*  A variable that represents a **Database** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _PathName_ <br/> |Required  <br/> |**String** <br/> |The path and file name of the new replica. If  _replica_ is an existing file name, then an error occurs.  <br/> |
| _Description_ <br/> |Required  <br/> |**String** <br/> |A **String** that describes the replica that you are creating  <br/> |
| _Options_ <br/> |Optional  <br/> |**Variant** <br/> |A **[ReplicaTypeEnum](replicatypeenum-enumeration-dao.md)** constant that specifies characteristics of the replica you are creating.  <br/> |
   
## Remarks

A newly created partial replica will have all **[ReplicaFilter](tabledef-replicafilter-property-dao.md)** properties set to **False**, meaning that no data will be in the tables. 
  
## Example

This function uses the **MakeReplica** method to create an additional replica of an existing Design Master. The  _intOptions_ argument can be a combination of the constants **dbRepMakeReadOnly** and **dbRepMakePartial**, or it can be 0. For example, to create a read-only partial replica, you should pass the value **dbRepMakeReadOnly** + **dbRepMakePartial** as the value of  _intOptions_.
  
```
Function MakeAdditionalReplica(strReplicableDB As _ 
 String, strNewReplica As String, intOptions As _ 
 Integer) As Integer 
 
 Dim dbsTemp As Database 
 On Error GoTo ErrorHandler 
 
 Set dbsTemp = OpenDatabase(strReplicableDB) 
 
 ' If no options are passed to 
 ' MakeAdditionalReplica, omit the 
 ' options argument, which defaults to 
 ' a full, read/write replica. Otherwise, 
 ' use the value of intOptions. 
 
 If intOptions = 0 Then 
 dbsTemp.MakeReplica strNewReplica, _ 
 "Replica of " &amp; strReplicableDB 
 Else 
 dbsTemp.MakeReplica strNewReplica, _ 
 "Replica of " &amp; strReplicableDB, _ 
 intOptions 
 End If 
 
 dbsTemp.Close 
 
ErrorHandler: 
 Select Case Err 
 Case 0: 
 MakeAdditionalReplica = 0 
 Exit Function 
 Case Else: 
 MsgBox "Error " &amp; Err &amp; " : " &amp; Error 
 MakeAdditionalReplica = Err 
 Exit Function 
 End Select 
 
End Function 
 
```


