---
title: "AutoLinkComparison element (DataRecordSet_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: af5eb7fd-89c6-49bf-4e45-431b63d6cd6a
description: "Defines a rule that compares a column in the parent DataRecordset element with a shape data item from the last successful automatic linking action performed in the user interface."
---

# AutoLinkComparison element (DataRecordSet_Type complexType) (Visio XML)

Defines a rule that compares a column in the parent **DataRecordset** element with a shape data item from the last successful automatic linking action performed in the user interface. 
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[AutoLinkComparison_Type](autolinkcomparison_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |recordsets.xml  <br/> |
   
## Definition

```XML
<xs:element name="AutoLinkComparison" type="AutoLinkComparison_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[DataRecordSet](datarecordset-element-datarecordsets_type-complextypevisio-xml.md) <br/> |[DataRecordSet_Type](datarecordset_type-complextypevisio-xml.md) <br/> |Specifies a recordset and the data binding between that recordset and shapes in drawing pages. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ColumnName  <br/> |xsd:string  <br/> |required  <br/> |Corresponds to a column name in the ADO recordset. |Values of the xsd:string type. |
|ContextType  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies properties of the group or shape to use for the comparison. Possible values are shown in the following table. |Values of the xsd:unsignedInt type. |
|ContextTypeLabel  <br/> |xsd:string  <br/> |optional  <br/> |If the ContextType value is 2 or 3, this attribute is required to define a comparison. For ContextType = 2, ContextTypeLabel must be the shape data item label, and if **ContextType** = 3, ContextTypeLabel must be the local row name. |Values of the xsd:string type. |
   

