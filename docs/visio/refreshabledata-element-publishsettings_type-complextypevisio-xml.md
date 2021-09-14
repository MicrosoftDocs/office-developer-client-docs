---
title: "RefreshableData element (PublishSettings_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 9a3b9d5a-fcba-eb18-3199-bd5a7f889af8
description: "Specifies whether a recordset is refreshable using Visio Services in Microsoft SharePoint Server 2013."
---

# RefreshableData element (PublishSettings_Type complexType) (Visio XML)

Specifies whether a recordset is refreshable using Visio Services in Microsoft SharePoint Server 2013.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RefreshableData_Type](refreshabledata_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml  <br/> |
   
## Definition

```XML
<xs:element name="RefreshableData" type="RefreshableData_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >

```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PublishSettings](publishsettings-element-visiodocument_type-complextypevisio-xml.md) <br/> |[PublishSettings_Type](publishsettings_type-complextypevisio-xml.md) <br/> |Specifies the settings that are used when the diagram is opened using Visio Services.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The identifier of a recordset.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

