---
title: "DataColumn element (DataColumns_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 92469c2f-f809-dff2-d0ee-b3b8f75083d2
description: "Defines how a data column appears in the External Data window in the Visio user interface and qualifies the data in the column by defining its data type and formatting."
---

# DataColumn element (DataColumns_Type complexType) (Visio XML)

Defines how a data column appears in the **External Data** window in the Visio user interface and qualifies the data in the column by defining its data type and formatting. 
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[DataColumn_Type](datacolumn_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
< xs:element name="DataColumn" type="DataColumn_Type" minOccurs="1" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataColumns](datacolumns-element-datarecordset_type-complextypevisio-xml.md) <br/> |[DataColumns_Type](datacolumns_type-complextypevisio-xml.md) <br/> |Contains all the **DataColumn** elements in a data recordset. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Calendar  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Calendar ID of the data column. |Values of the xsd:unsignedShort type. |
|ColumnNameID  <br/> |xsd:string  <br/> |required  <br/> |External name of the data column. Appears in the headings in the **External Data** window and in labels in data graphics. |Values of the xsd:string type. |
|Currency  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Currency ID of the data column. |Values of the xsd:unsignedShort type. |
|DataType  <br/> |xsd:unsignedShort  <br/> |optional  <br/> |Type of the data in the data column. |Values of the xsd:unsignedShort type. |
|Degree  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Specifies the degree (power) of the units, for example squared, or cubed. The default (attribute absent) is 1. |Values of the xsd:unsignedInt type. |
|DisplayOrder  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Defines the display position of the data column in the **External Data** window, from the left-most column (0) to the right-most column (largest value). |Values of the xsd:unsignedInt type. |
|DisplayWidth  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |Width of the data column in the **External Data** window. |Values of the xsd:unsignedInt type. |
|Hyperlink  <br/> |xsd:boolean  <br/> |optional  <br/> |Whether the data column creates a hyperlink in a shape when the shape is linked to data. |Values of the xsd:boolean type. |
|Label  <br/> |xsd:string  <br/> |required  <br/> |Label of the data column. |Values of the xsd:string type. |
|LangID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> |The language ID of the data column. |Values of the xsd:unsignedInt type. |
|Mapped  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether the column is visible in the **External Data** window. True (1) for the column to be visible; False (0) for the column not to be visible. The default (attribute absent) is for the column to be visible. |Values of the xsd:boolean type. |
|Name  <br/> |xsd:string  <br/> |required  <br/> |Internal name of the data column. Used as the row name for the shape-data item (custom property) added to a shape when the shape is linked to a data row. |Values of the xsd:string type. |
|OrigLabel  <br/> |xsd:string  <br/> |optional  <br/> |Column label returned to Visio by the underlying ADO interface. |Values of the xsd:string type. |
|UnitType  <br/> |xsd:string  <br/> |optional  <br/> |Unit type of the data in the data column. |Values of the xsd:string type. |
   

