---
title: "REVOKE Statement (Microsoft Access SQL)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- jetsql40.chm5277479
  
localization_priority: Normal
ms.assetid: 69399fd6-c4e8-f2e2-e5f4-48ae779323f5
description: "Revokes specific privileges from an existing user or group."
---

# REVOKE Statement (Microsoft Access SQL)

Revokes specific privileges from an existing user or group.
  
## Syntax

REVOKE { *privilege*  [,  *privilege*  , …]} ON {TABLE  *table*  | OBJECT  *object*  | 
  
 CONTAINTER  *container*  } FROM {  *authorizationname*  [,  *authorizationname*  , …]} 
  
The REVOKE statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *privilege*  <br/> |The privilege or privileges to be revoked. Privileges are specified using the following keywords: SELECT, DELETE, INSERT, UPDATE, DROP, SELECTSECURITY, UPDATESECURITY, DBPASSWORD, UPDATEIDENTITY, CREATE, SELECTSCHEMA, SCHEMA and UPDATEOWNER.  <br/> |
| *table*  <br/> |Any valid table name.  <br/> |
| *object*  <br/> |This can encompass any non-table object. A stored query (view or procedure) is one example.  <br/> |
| *container*  <br/> |The name of a valid container.  <br/> |
| *authorizationname*  <br/> |A user or group name.  <br/> |
   

