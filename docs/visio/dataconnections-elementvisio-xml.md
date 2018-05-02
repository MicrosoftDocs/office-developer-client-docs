---
title: "DataConnections element ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 3cac0cd0-87ff-8c82-2d33-20070a505f4e
description: "Contains the DataConnection elements for the document."
---

# DataConnections element ('Visio XML')

Contains the **DataConnection** elements for the document. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[DataConnections_Type](dataconnections_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |connections.xml  <br/> |
   
## Definition

```XML
< xs:element name="DataConnections" type="DataConnections_Type" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

None.
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataConnection](dataconnection-element-dataconnections_type-complextypevisio-xml.md) <br/> |[DataConnection_Type](dataconnection_type-complextypevisio-xml.md) <br/> |Abstracts communication between one or more **DataRecordset** elements and a non-XML data source.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|NextID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The next available ID for new connections.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

