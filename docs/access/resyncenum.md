---
title: "ResyncEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 3d38b77b-6afe-e6a0-1a05-7c7ffc19edef

---

# ResyncEnum

Specifies whether underlying values are overwritten by a call to [Resync](resync-method-ado.md).
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adResyncAllValues** <br/> |2  <br/> |Default. Overwrites data, and pending updates are canceled.  <br/> |
|**adResyncUnderlyingValues** <br/> |1  <br/> |Does not overwrite data, and pending updates are not canceled.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.Resync.ALLVALUES  <br/> |
|AdoEnums.Resync.UNDERLYINGVALUES  <br/> |
   

