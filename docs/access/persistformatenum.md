---
title: "PersistFormatEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 5aa99a63-d422-0812-5aba-19305a3ad405

---

# PersistFormatEnum

Specifies the format in which to save a [Recordset](recordset-object-ado.md).
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adPersistADTG** <br/> |0  <br/> |Indicates Microsoft Advanced Data TableGram (ADTG) format.  <br/> |
|**adPersistADO** <br/> |1  <br/> |Indicates that ADO's own Extensible Markup Language (XML) format will be used. This value is the same as adPersistXML and is included for backwards compatibility.  <br/> |
|**adPersistXML** <br/> |1  <br/> |Indicates Extensible Markup Language (XML) format.  <br/> |
|**adPersistProviderSpecific** <br/> |2  <br/> |Indicates that the provider will persist the **Recordset** using its own format.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.PersistFormat.ADTG  <br/> |
|AdoEnums.PersistFormat.XML  <br/> |
   

