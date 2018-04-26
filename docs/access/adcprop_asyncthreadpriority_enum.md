---
title: "ADCPROP_ASYNCTHREADPRIORITY_ENUM"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: b15006dd-22d5-fcf3-8196-9e24ea9d55a7
---

# ADCPROP_ASYNCTHREADPRIORITY_ENUM

For an RDS [Recordset](recordset-object-ado.md) object, specifies the execution priority of the asynchronous thread that retrieves data. 
  
Use these constants with the **Recordset** " **Background Thread Priority** " dynamic property, which is referenced in the ADO Dynamic Property Index and documented in the [Microsoft Cursor Service for OLE DB](microsoft-cursor-service-for-ole-db-ado-service-component.md) documentation. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adPriorityAboveNormal** <br/> |4  <br/> |Sets priority between normal and highest.  <br/> |
|**adPriorityBelowNormal** <br/> |2  <br/> |Sets priority between lowest and normal.  <br/> |
|**adPriorityHighest** <br/> |5  <br/> |Sets priority to the highest possible.  <br/> |
|**AdPriorityLowest** <br/> |1  <br/> |Sets priority to the lowest possible.  <br/> |
|**adPriorityNormal** <br/> |3  <br/> |Sets priority to normal.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.AdcPropAsyncThreadPriority.ABOVENORMAL  <br/> |
|AdoEnums.AdcPropAsyncThreadPriority.BELOWNORMAL  <br/> |
|AdoEnums.AdcPropAsyncThreadPriority.HIGHEST  <br/> |
|AdoEnums.AdcPropAsyncThreadPriority.LOWEST  <br/> |
|AdoEnums.AdcPropAsyncThreadPriority.NORMAL  <br/> |
   

