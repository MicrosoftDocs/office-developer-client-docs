---
title: "CREATE USER or GROUP Statement (Microsoft Access SQL)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 62148ce2-0f81-944e-a1ab-edef990fff9f
description: "Creates one or more new users or groups."
---

# CREATE USER or GROUP Statement (Microsoft Access SQL)

Creates one or more new users or groups.
  
## Syntax

Create a user:
  
CREATE USER  *user*  *password pid*  [,  *user*  *password pid*  , …] 
  
Create a group:
  
CREATE GROUP  *group*  *pid*  [,  *group*  *pid*  , …] 
  
The CREATE USER or GROUP statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *user*  <br/> |The name of a user to be added to the workgroup information file.  <br/> |
| *group*  <br/> |The name of a group to be added to the workgroup information file.  <br/> |
| *password*  <br/> |The password to be associated with the specified  *user*  name.  <br/> |
| *pid*  <br/> |The personal id.  <br/> |
   
## Remarks

A  *user*  and a  *group*  cannot have the same name. 
  
A  *password*  is required for each  *user*  or  *group*  that is created. 
  

