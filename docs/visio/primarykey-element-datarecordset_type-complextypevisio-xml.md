---
title: "PrimaryKey element (DataRecordSet_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 47533e6e-0a48-af61-a0c2-b2cec140ae4b
description: "Identifies one or more primary-key columns in the data recordset."
---

# PrimaryKey element (DataRecordSet_Type complexType) (Visio XML)

Identifies one or more primary-key columns in the data recordset.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[PrimaryKey_Type](primarykey_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
< xs:element name="PrimaryKey" type="PrimaryKey_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataRecordSet](datarecordset-element-datarecordsets_type-complextypevisio-xml.md) <br/> |[DataRecordSet_Type](datarecordset_type-complextypevisio-xml.md) <br/> |Stores, formats, refreshes, and exposes data queried from a database in Microsoft Visio. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RowKeyValue](rowkeyvalue-element-primarykey_type-complextypevisio-xml.md) <br/> |[RowKeyValue_Type](rowkeyvalue_type-complextypevisio-xml.md) <br/> |Specifies the value of this component of the primary key for an individual row of a recordset. There MUST be at least one occurrence of this child element. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ColumnNameID  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the name of a field that is a component of the primary key. It MUST be the value of the **ColumnNameID** attribute of a DataColumn_Type descendant element of the DataRecordSet_Type whose primary key is being specified. |Values of the xsd:string type. |
   

