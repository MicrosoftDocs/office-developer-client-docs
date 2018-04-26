---
title: "Field-Related Error Information"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: 81a2c5a4-ab09-53d8-b270-e889b00a0c1a
description: "If an error is directly related to a field — for example, if the data is missing or if it is the wrong type for the field — you can retrieve more information about the cause of the problem by examining the Field object's Status property. This property has been enhanced to provide specific information about the problem. So, for example, when a call to UpdateBatch fails, the cause of the problem can be determined by examining the Status property of the Fields in each of the effected records. The property will contain one of the values in the FieldStatusEnum constant. The following table includes those values that are of particular interest when an error occurs."
---

# Field-Related Error Information

If an error is directly related to a field — for example, if the data is missing or if it is the wrong type for the field — you can retrieve more information about the cause of the problem by examining the **Field** object's **Status** property. This property has been enhanced to provide specific information about the problem. So, for example, when a call to **UpdateBatch** fails, the cause of the problem can be determined by examining the **Status** property of the **Fields** in each of the effected records. The property will contain one of the values in the **FieldStatusEnum** constant. The following table includes those values that are of particular interest when an error occurs. 
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adFieldCantConvertValue** <br/> |2  <br/> |Indicates that the field cannot be retrieved or stored without loss of data.  <br/> |
|**adFieldDataOverflow** <br/> |6  <br/> |Indicates that the data returned from the provider overflowed the data type of the field.  <br/> |
|**adFieldDefault** <br/> |13  <br/> |Indicates that the default value for the field was used when setting data.  <br/> |
|**adFieldIgnore** <br/> |15  <br/> |Indicates that this field was skipped when setting data values in the source. No value was set by the provider.  <br/> |
|**adFieldIntegrityViolation** <br/> |10  <br/> |Indicates that the field cannot be modified because it is a calculated or derived entity.  <br/> |
|**adFieldIsNull** <br/> |3  <br/> |Indicates that the provider returned a null value.  <br/> |
|**adFieldOutOfSpace** <br/> |22  <br/> |Indicates that the provider is unable to obtain enough storage space to complete a move or copy operation.  <br/> |
   

