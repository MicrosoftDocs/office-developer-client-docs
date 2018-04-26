---
title: "Adding Records"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 7a5b27bc-7b28-4f43-b55e-a21edfb9e1b3
description: "Use the AddNew method to create and initialize a new record in an existing Recordset . You can use the Supports method with a CursorOptionEnum value of adAddNew to verify whether you can add records to the current Recordset object."
---

# Adding Records

Use the **AddNew** method to create and initialize a new record in an existing **Recordset**. You can use the **Supports** method with a **CursorOptionEnum** value of **adAddNew** to verify whether you can add records to the current **Recordset** object. 
  
After you call the **AddNew** method, the new record becomes the current record and remains current after you call the **Update** method. If the **Recordset** object does not support bookmarks, you might not be able to access the new record once you move to another record. Therefore, depending on your cursor type, you might need to call the **Requery** method to make the new record accessible. 
  
If you call **AddNew** while editing the current record or while adding a new record, ADO calls the **Update** method to save any changes and then creates the new record. 
  

