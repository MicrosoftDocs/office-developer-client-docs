---
title: "Connect element (Connects_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 6e1ad47b-ee28-6b9a-f2f9-642e09ca28d4
description: "Represents a connection between two shapes in a drawing, such as a line and a box in an organization chart."
---

# Connect element (Connects_Type complexType) ('Visio XML')

Represents a connection between two shapes in a drawing, such as a line and a box in an organization chart.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Connect_Type](connect_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |page#.xml, master#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Connect" type="Connect_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Connects](connects-element-pagecontents_type-complextypevisio-xml.md) <br/> |[Connects_Type](connects_type-complextypevisio-xml.md) <br/> |Contains a **Connect** element for each connection between two shapes in a drawing.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|FromCell  <br/> |xsd:string  <br/> |optional  <br/> |The cell from which a connection originates.  <br/> |Values of the xsd:string type.  <br/> |
|FromPart  <br/> |xsd:int  <br/> |optional  <br/> |The part of a shape from which a connection originates.  <br/> |Values of the xsd:int type.  <br/> |
|FromSheet  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The ID of the shape from which a connection or connections originate.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|ToCell  <br/> |xsd:string  <br/> |optional  <br/> |The cell to which a connection is made.  <br/> |Values of the xsd:string type.  <br/> |
|ToPart  <br/> |xsd:int  <br/> |optional  <br/> |The part of a shape to which a connection is made.  <br/> |Values of the xsd:Int type.  <br/> |
|ToSheet  <br/> |xsd:unsignedInt  <br/> |required  <br/> |The ID of the shape to which one or more connections are made.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
   

