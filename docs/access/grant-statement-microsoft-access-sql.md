---
title: "GRANT Statement (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277478
  
localization_priority: Normal
ms.assetid: 50ae97ae-d5be-57e5-d9da-f3fc42f01d83
description: "Grants specific privileges to an existing user or group."
---

# GRANT Statement (Microsoft Access SQL)

Grants specific privileges to an existing user or group.
  
## Syntax

GRANT { *privilege*  [,  *privilege*  , …]} ON{TABLE  *table*  | OBJECT  *object*  | 
  
CONTAINER  *container*  } TO {  *authorizationname*  [,  *authorizationname*  , …]} 
  
The GRANT statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *privilege*  <br/> |The privilege or privileges to be granted. Privileges are specified using the following keywords: SELECT, DELETE, INSERT, UPDATE, DROP, SELECTSECURITY, UPDATESECURITY, DBPASSWORD, UPDATEIDENTITY, CREATE, SELECTSCHEMA, SCHEMA and UPDATEOWNER.  <br/> |
| *tablename*  <br/> |Any valid table name.  <br/> |
| *object*  <br/> |This can encompass any non-table object. A stored query (view or procedure) is one example.  <br/> |
| *container*  <br/> |The name of a valid container.  <br/> |
| *authorizationname*  <br/> |A user or group name.  <br/> |
   

