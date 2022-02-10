---
title: "ProtectMasters element (DocumentSettings_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: edc46630-c320-6b4e-4747-961075dd5fd7
description: "Specifies whether the user is prevented from creating, editing, or deleting master shapes. The user can still create new shapes from a master shape, regardless of this setting."
---

# ProtectMasters element (DocumentSettings_Type complexType) (Visio XML)

Specifies whether the user is prevented from creating, editing, or deleting master shapes. The user can still create new shapes from a master shape, regardless of this setting. 
  
The range of possible values for this element is either '0' or '1'. A value of '0' indicates that users can create, edit, or delete master shapes. A value of '1' indicates that users cannot create, edit, or delete master shapes.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[ProtectMasters_Type](protectmasters_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
< xs:element name="ProtectMasters" type="ProtectMasters_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DocumentSettings](documentsettings-element-visiodocument_type-complextypevisio-xml.md) <br/> |[DocumentSettings_Type](documentsettings_type-complextypevisio-xml.md) <br/> |Contains elements that specify document settings. |
   
### Child elements

None.
  
### Attributes

None.
  

