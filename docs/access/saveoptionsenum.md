---
title: "SaveOptionsEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2a4e4c7a-6331-7270-0514-cc549c721ffd

---

# SaveOptionsEnum

Specifies whether a file should be created or overwritten when saving from a [Stream](stream-object-ado.md) object. The values can be combined with an AND operator. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adSaveCreateNotExist** <br/> |1  <br/> |Default. Creates a new file if the file specified by the  *FileName*  parameter does not already exist.  <br/> |
|**adSaveCreateOverWrite** <br/> |2  <br/> |Overwrites the file with the data from the currently open **Stream** object, if the file specified by the  *Filename*  parameter already exists.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

