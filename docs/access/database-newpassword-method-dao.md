---
title: "Database.NewPassword Method (DAO)"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
f1_keywords:
- dao360.chm1052943
  
localization_priority: Normal
ms.assetid: 01c1c454-d651-222c-225a-2b02734a1b7a
description: "Changes the password of an existing Microsoft Access database engine database (Microsoft Access workspaces only)."
---

# Database.NewPassword Method (DAO)

Changes the password of an existing Microsoft Access database engine database (Microsoft Access workspaces only).
  
## Syntax

 *expression*  . **NewPassword**( ** *bstrOld* **, ** *bstrNew* ** ) 
  
 *expression*  An expression that returns a **Database** object. 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _bstrOld_ <br/> |Required  <br/> |**String** <br/> |The current setting of the **Password** property of the **Database** object.  <br/> |
| _bstrNew_ <br/> |Required  <br/> |**String** <br/> |The new setting of the **Password** property of the **Database** object.  <br/> > [!NOTE]> Use strong passwords that combine upper- and lowercase letters, numbers, and symbols. Weak passwords don't mix these elements. Strong password: Y6dh!et5. Weak password: House27. Use a strong password that you can remember so that you don't have to write it down.           |
   
## Remarks

The bstrOld and bstrNew strings can be up to 20 characters long and can include any characters except the ASCII character 0 (null). To clear the password, use a zero-length string ("") for bstrNew.
  
Passwords are case-sensitive.
  
If a database has no password, the Microsoft Access database engine will automatically create one by passing a zero-length string ("") for the old password.
  
> [!IMPORTANT]
> If you lose your password, you can never open the database again. 
  

