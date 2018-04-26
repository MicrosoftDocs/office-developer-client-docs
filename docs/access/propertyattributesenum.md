---
title: "PropertyAttributesEnum"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: cbe93f65-a3ee-4741-1ac7-1c98ac53cdde

---

# PropertyAttributesEnum

Specifies the attributes of a [Property](property-object-ado.md) object. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adPropNotSupported** <br/> |0  <br/> |Indicates that the property is not supported by the provider.  <br/> |
|**adPropRequired** <br/> |1  <br/> |Indicates that the user must specify a value for this property before the data source is initialized.  <br/> |
|**adPropOptional** <br/> |2  <br/> |Indicates that the user does not need to specify a value for this property before the data source is initialized.  <br/> |
|**adPropRead** <br/> |512  <br/> |Indicates that the user can read the property.  <br/> |
|**adPropWrite** <br/> |1024  <br/> |Indicates that the user can set the property.  <br/> |
   
 **ADO/WFC Equivalent**
  
Package: **com.ms.wfc.data**
  
|**Constant**|
|:-----|
|AdoEnums.PropertyAttributes.NOTSUPPORTED  <br/> |
|AdoEnums.PropertyAttributes.REQUIRED  <br/> |
|AdoEnums.PropertyAttributes.OPTIONAL  <br/> |
|AdoEnums.PropertyAttributes.READ  <br/> |
|AdoEnums.PropertyAttributes.WRITE  <br/> |
   

