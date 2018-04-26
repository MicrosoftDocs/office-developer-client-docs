---
title: "DROP USER or GROUP Statement (Microsoft Access SQL)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 46bc5916-556b-17df-2f4c-8fd7bbd21ef7
description: "Deletes one or more existing user s or group s, or removes one or more existing user s from an existing group ."
---

# DROP USER or GROUP Statement (Microsoft Access SQL)

Deletes one or more existing  *user*  s or  *group*  s, or removes one or more existing  *user*  s from an existing  *group*  . 
  
## Syntax

Delete one or more  *user*  s or remove one or more  *user*  s from a  *group*  : 
  
DROP USER  *user*  [,  *user*  , …] [FROM  *group*  ] 
  
Delete one or more  *group*  s: 
  
DROP GROUP  *group*  [,  *group*  , …] 
  
The DROP USER or GROUP statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *user*  <br/> |The name of a user to be removed from the workgroup information file.  <br/> |
| *group*  <br/> |The name of a group to be removed from the workgroup information file.  <br/> |
   
## Remarks

If the FROM keyword is used in the DROP USER statement, then each of the  *user*  s listed in the statement will be removed from the  *group*  specified following the FROM keyword. However, the  *user*  s themselves will not be deleted. 
  
The DROP GROUP statement will delete the specified  *group*  (s). The  *user*  s who are members of the  *group*  (s) will not be affected, but they will no longer be members of the deleted  *group*  (s). 
  

