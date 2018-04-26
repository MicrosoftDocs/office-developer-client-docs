---
title: "ChangePassword Method (ADOX)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 999826a5-3e6b-b6da-b8f6-d61b9a50ceca
---

# ChangePassword Method (ADOX)

Changes the password for a user account.
  
## Syntax

 *User*  . **ChangePassword** *OldPassword*  ,  *NewPassword* 
  
## Parameters

-  *OldPassword* 
    
- A **String** value that specifies the user's existing password. If the user doesn't currently have a password, use an empty string ("") for  *OldPassword*  . 
    
-  *NewPassword* 
    
- A **String** value that specifies the new password. 
    
## Remarks

For security reasons, the old password must be specified in addition to the new password.
  
An error will occur if the provider does not support the administration of trustee properties.
  

