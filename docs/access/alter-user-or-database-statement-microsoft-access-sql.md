---
title: "ALTER USER or DATABASE Statement (Microsoft Access SQL)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 86ccd296-5171-97e7-683f-cdaab4bde9ab
description: "Changes the password for an existing user or for a database."
---

# ALTER USER or DATABASE Statement (Microsoft Access SQL)

Changes the password for an existing user or for a database.
  
## Syntax

ALTER DATABASE PASSWORD  *newpassword oldpassword* 
  
ALTER USER  *user*  PASSWORD  *newpassword oldpassword* 
  
The ALTER USER or DATABASE statement has these parts:
  
|**Part**|**Description**|
|:-----|:-----|
| *user*  <br/> |The name of a user to be added to the workgroup information file.  <br/> |
| *newpassword*  <br/> |The new password to be associated with the specified  *user*  or  *database*  name.  <br/> |
| *oldpassword*  <br/> |The existing password to be associated with the specified  *user*  or  *group*  name.  <br/> |
   

