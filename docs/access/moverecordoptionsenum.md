---
title: "MoveRecordOptionsEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 2785bca0-777c-a802-51d7-6f5cf0fb4210

---

# MoveRecordOptionsEnum

Specifies the behavior of the [Record](record-object-ado.md) object [MoveRecord](moverecord-method-ado.md) method. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adMoveUnspecified** <br/> |-1  <br/> |Default. Performs the default move operation: The operation fails if the destination file or directory already exists, and the operation updates hypertext links.  <br/> |
|**adMoveOverWrite** <br/> |1  <br/> |Overwrites the destination file or directory, even if it already exists.  <br/> |
|**adMoveDontUpdateLinks** <br/> |2  <br/> |Modifies the default behavior of **MoveRecord** method by not updating the hypertext links of the source **Record**. The default behavior depends on the capabilities of the provider. Move operation updates links if the provider is capable. If the provider cannot fix links or if this value is not specified, then the move succeeds even when links have not been fixed.  <br/> |
|**adMoveAllowEmulation** <br/> |4  <br/> |Requests that the provider attempt to simulate the move (using download, upload, and delete operations). If the attempt to move the **Record** fails because the destination URL is on a different server or serviced by a different provider than the source, this may cause increased latency or data loss, due to different provider capabilities when moving resources between providers.  <br/> |
   
 **ADO/WFC Equivalent**
  
These constants do not have ADO/WFC equivalents.
  

