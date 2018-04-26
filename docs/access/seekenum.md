---
title: "SeekEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: a0574809-db2d-8759-18cc-fb1cf776e8fd

---

# SeekEnum

Specifies the type of [Seek](seek-method-ado.md) to execute. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|adSeekFirstEQ  <br/> |1  <br/> |Seeks the first key equal to  *KeyValues*  .  <br/> |
|adSeekLastEQ  <br/> |2  <br/> |Seeks the last key equal to  *KeyValues*  .  <br/> |
|adSeekAfterEQ  <br/> |4  <br/> |Seeks either a key equal to  *KeyValues*  or just after where that match would have occurred.  <br/> |
|adSeekAfter  <br/> |8  <br/> |Seeks a key just after where a match with  *KeyValues*  would have occurred.  <br/> |
|adSeekBeforeEQ  <br/> |16  <br/> |Seeks either a key equal to  *KeyValues*  or just before where that match would have occurred.  <br/> |
|adSeekBefore  <br/> |32  <br/> |Seeks a key just before where a match with  *KeyValues*  would have occurred.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.Seek.FIRSTEQ  <br/> |
|AdoEnums.Seek.LASTEQ  <br/> |
|AdoEnums.Seek.AFTEREQ  <br/> |
|AdoEnums.Seek.AFTER  <br/> |
|AdoEnums.Seek.BEFOREEQ  <br/> |
|AdoEnums.Seek.BEFORE  <br/> |
   

