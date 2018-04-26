---
title: "Converting DAO Code to ADO"
  
  
manager: soliver
ms.date: 7/29/2015
ms.audience: Developer
 
f1_keywords:
- vbaac10.chm5267115
  
localization_priority: Normal
ms.assetid: 4720906b-d6b1-aa6d-3b18-ff828d16acae
description: ""
---

# Converting DAO Code to ADO

> [!NOTE]
> Versions of the DAO library prior to 3.6 are not provided or supported in Access. 
  
## DAO to ADO object Map

|****DAO****|****ADO(ADODB)****|****Note****|
|:-----|:-----|:-----|
|DBEngine  <br/> |None  <br/> ||
|Workspace  <br/> |None  <br/> ||
|Database  <br/> |Connection  <br/> ||
|Recordset  <br/> |Recordset  <br/> ||
|Dynaset-Type  <br/> |Keyset  <br/> |Retrieves a set of pointers to the records in the recordset  <br/> |
|Snapshot-Type  <br/> |Static  <br/> |Both retrieve full records but a Static recordset can be updated.  <br/> |
|Table-Type  <br/> |Keyset with adCmdTableDirect Option  <br/> ||
|Field  <br/> |Field  <br/> |When referred to in a recordset  <br/> |
   
|**Task**|**DAO**|**ADO**|
|:-----|:-----|:-----|
|Open a **Recordset** <br/> |
```
Dim db as Database
Dim rs as DAO.Recordset
Set db = CurrentDB()
Set rs = db.OpenRecordset("Employees")

```

|
```
Dim rs as New ADODB.Recordset
rs.Open "Employees", CurrentProject.Connection, _
         adOpenKeySet, adLockOptimistic

```

|
|Edit a **Recordset** <br/> |
```
rs.Edit 
rs("TextFieldName") = "NewValue"
rs.Update
```

|
```
rs("TextFieldName") = "NewValue" 
rs.Update
```

> [!NOTE]
> Moving focus from current record via **MoveNext, MoveLast, MoveFirst, MovePrevious** without first using the **CancelUpdate** method will implicitly execute the **Update** method. 
  
|
   
 **Link provided by:**![Community Member Icon](media/8b9774c4-6c97-470e-b3a2-56d8f786444c.png) The [UtterAccess](http://www.utteraccess.com) community 
  
- [Choosing between DAO and ADO](http://www.utteraccess.com/wiki/index.php/Choosing_between_DAO_and_ADO)
    
## About the Contributors
<a name="AboutContributors"> </a>

UtterAccess is the premier Microsoft Access wiki and help forum. Click here to join. 
  

