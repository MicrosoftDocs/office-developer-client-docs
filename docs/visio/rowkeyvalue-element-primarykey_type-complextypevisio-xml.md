---
title: "RowKeyValue element (PrimaryKey_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 9077ad4b-c539-c0c8-d268-9a009990abdd
description: "Specifies the value of a primary key for an individual row of a recordset."
---

# RowKeyValue element (PrimaryKey_Type complexType) ('Visio XML')

Specifies the value of a primary key for an individual row of a recordset.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RowKeyValue_Type](rowkeyvalue_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
< xs:element name="RowKeyValue" type="RowKeyValue_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PrimaryKey](primarykey-element-datarecordset_type-complextypevisio-xml.md) <br/> |[PrimaryKey_Type](primarykey_type-complextypevisio-xml.md) <br/> |Specifies a primary key of a recordset.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|RowID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |A unique value that identifies a row of a recordset.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Value  <br/> |xsd:string  <br/> |required  <br/> |The value of the primary key for this row of the recordset.  <br/> |Values of the xsd:string type.  <br/> |
   

