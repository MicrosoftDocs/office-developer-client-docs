---
title: "DataColumns element (DataRecordSet_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 34e25349-d0fa-b3a0-425b-778184e9f58f
description: "Contains all the DataColumn elements in a data recordset."
---

# DataColumns element (DataRecordSet_Type complexType) ('Visio XML')

Contains all the **DataColumn** elements in a data recordset. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[DataColumns_Type](datacolumns_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
< xs:element name="DataColumns" type="DataColumns_Type" minOccurs="1" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataRecordSet](datarecordset-element-datarecordsets_type-complextypevisio-xml.md) <br/> |[DataRecordSet_Type](datarecordset_type-complextypevisio-xml.md) <br/> |Stores, formats, refreshes, and exposes data queried from a database in Microsoft Visio.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataColumn](datacolumn-element-datacolumns_type-complextypevisio-xml.md) <br/> |[DataColumn_Type](datacolumn_type-complextypevisio-xml.md) <br/> |Defines how a data column appears in the **External Data** window in the Visio user interface and qualifies the data in the column by defining its data type and formatting.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|SortAsc  <br/> |xsd:boolean  <br/> |optional  <br/> |The column on which to sort the data.  <br/> |Values of the xsd:boolean type.  <br/> |
|SortColumn  <br/> |xsd:string  <br/> |optional  <br/> |Whether to sort the **SortColumn** column in ascending (1) or descending (0) order.  <br/> |Values of the xsd:string type.  <br/> |
   

