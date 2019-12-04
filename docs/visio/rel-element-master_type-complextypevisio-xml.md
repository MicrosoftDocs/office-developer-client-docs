---
title: "Rel element (Master_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 151cdd13-d00b-249c-7ebd-1ae9c4042b03
description: "Specifies a relationship to a part with the corresponding master XML."
---

# Rel element (Master_Type complexType) (Visio XML)

Specifies a relationship to a part with the corresponding master XML.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Rel_Type](rel_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |pages.xml, masters.xml, recordsets.xml, page#.xml, master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Rel"  type="Rel_Type" minOccurs="1" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Master](master-element-masters_type-complextypevisio-xml.md) <br/> |[Master_Type](master_type-complextypevisio-xml.md) <br/> |Specifies one instance of master XML stored in the drawing.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|r:id  <br/> |xsd:string  <br/> See Remarks.  <br/> |required  <br/> |Specifies a relationship to a part.  <br/> |"rId#"  <br/> See Remarks.  <br/> |
   
## Remarks

The value of the **r:id** attribute must be an **ST_RelationshipID** type. The **ST_RelationshipID** type is a string that must be in the format 'rId#', where the final character must be a number. The number must be unique among all sibling elements of the **Rel** element. 
  
For more information about the ST_RelationshipID type, see the [ISO/IEC 29500 Part 1 specification](https://www.iso.org/iso/home/store/catalogue_tc/catalogue_detail.md?csnumber=61750).
  

