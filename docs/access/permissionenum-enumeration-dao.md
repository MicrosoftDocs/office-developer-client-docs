---
title: "PermissionEnum Enumeration (DAO)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: dcce9940-f8a7-e915-1b69-05c341bea8cd
description: "Used with the Permissions property to specify the type of permissions."
---

# PermissionEnum Enumeration (DAO)

Used with the **Permissions** property to specify the type of permissions. 
  
|**Name**|**Value**|**Description**|
|:-----|:-----|:-----|
|**dbSecCreate** <br/> |1  <br/> |The user can create new documents (not valid for Document objects).  <br/> |
|**dbSecDBAdmin** <br/> |8  <br/> |The user can replicate a database and change the database password (not valid for Document objects).  <br/> |
|**dbSecDBCreate** <br/> |1  <br/> |The user can create new databases. This option is valid only on the Databases container in the workgroup information file (Systen.mdw). This constant is not valid for Document objects.  <br/> |
|**dbSecDBExclusive** <br/> |4  <br/> |The user has exclusive access to the database.  <br/> |
|**dbSecDBOpen** <br/> |2  <br/> |The user can open the database.  <br/> |
|**dbSecDelete** <br/> |65536  <br/> |The user can delete the object.  <br/> |
|**dbSecDeleteData** <br/> |128  <br/> |The user can delete records.  <br/> |
|**dbSecFullAccess** <br/> |1048575  <br/> |The user has full access to the object.  <br/> |
|**dbSecInsertData** <br/> |32  <br/> |The user can add records.  <br/> |
|**dbSecNoAccess** <br/> |0  <br/> |The user does not have access to the object (not valid for Document objects).  <br/> |
|**dbSecReadDef** <br/> |4  <br/> |The user can read the table definition, including column and index information.  <br/> |
|**dbSecReadSec** <br/> |131072  <br/> |The user can read the object's security-related information.  <br/> |
|**dbSecReplaceData** <br/> |64  <br/> |The user can modify records.  <br/> |
|**dbSecRetrieveData** <br/> |20  <br/> |The user can retrieve data from the Document object.  <br/> |
|**dbSecWriteDef** <br/> |65548  <br/> |The user can modify or delete the table definition, including column and index information.  <br/> |
|**dbSecWriteOwner** <br/> |524288  <br/> |The user can change the Owner property setting.  <br/> |
|**dbSecWriteSec** <br/> |262144  <br/> |The user can alter access permissions.  <br/> |
   

