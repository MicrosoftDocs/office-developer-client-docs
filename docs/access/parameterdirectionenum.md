---
title: "ParameterDirectionEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 73a97522-010e-d8f4-1a30-15df2469cad4

---

# ParameterDirectionEnum

Specifies whether the [Parameter](parameter-object-ado.md) represents an input parameter, an output parameter, both an input and an output parameter, or the return value from a stored procedure. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adParamInput** <br/> |1  <br/> |Default. Indicates that the parameter represents an input parameter.  <br/> |
|**adParamInputOutput** <br/> |3  <br/> |Indicates that the parameter represents both an input and output parameter.  <br/> |
|**adParamOutput** <br/> |2  <br/> |Indicates that the parameter represents an output parameter.  <br/> |
|**adParamReturnValue** <br/> |4  <br/> |Indicates that the parameter represents a return value.  <br/> |
|**adParamUnknown** <br/> |0  <br/> |Indicates that the parameter direction is unknown.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.ParameterDirection.INPUT  <br/> |
|AdoEnums.ParameterDirection.INPUTOUTPUT  <br/> |
|AdoEnums.ParameterDirection.OUTPUT  <br/> |
|AdoEnums.ParameterDirection.RETURNVALUE  <br/> |
|AdoEnums.ParameterDirection.UNKNOWN  <br/> |
   

