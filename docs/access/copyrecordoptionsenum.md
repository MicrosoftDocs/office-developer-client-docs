---
title: "CopyRecordOptionsEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: ab9426e9-0e4e-6c85-43cf-e4a205a7c4c0
---

# CopyRecordOptionsEnum

Specifies the behavior of the [CopyRecord](copyrecord-method-ado.md) method. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adCopyAllowEmulation** <br/> |4  <br/> |Indicates that the  *Source*  provider attempts to simulate the copy using download and upload operations if this method fails due to  *Destination*  being on a different server or is serviced by a different provider than  *Source*  . Note that differing provider capabilities may hamper performance or lose data.  <br/> |
|**adCopyNonRecursive** <br/> |2  <br/> |Copies the current directory, but none of its subdirectories, to the destination. The copy operation is not recursive.  <br/> |
|**adCopyOverWrite** <br/> |1  <br/> |Overwrites the file or directory if the  *Destination*  points to an existing file or directory.  <br/> |
|**adCopyUnspecified** <br/> |-1  <br/> |Default. Performs the default copy operation: The operation fails if the destination file or directory already exists, and the operation copies recursively.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

