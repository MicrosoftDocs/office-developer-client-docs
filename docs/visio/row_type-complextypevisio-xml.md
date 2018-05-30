---
title: "Row_Type complexType ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 5e5c420e-f384-7b62-c862-35aea16e6d55

---

# Row_Type complexType ('Visio XML')

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
          <xs:complexType name="Row_Type">
          
          <xs:sequence>
    <xs:element name="Cell"  type="Cell_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
    <xs:element name="Trigger"  type="Trigger_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
      </xs:sequence>
    <xs:attribute name="N"
  type="xsd:string"
    />
    <xs:attribute name="LocalName"
  type="xsd:string"
    />
    <xs:attribute name="IX"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="T"
  type="xsd:string"
    />
    <xs:attribute name="Del"
  type="xsd:boolean"
    />
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Cell](http://msdn.microsoft.com/library/5e060a3f-e804-834f-531b-78a544fee61f%28Office.15%29.aspx) <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> ||
|[Trigger](http://msdn.microsoft.com/library/6dbd2c66-3b29-03f6-648f-723d359ded0d%28Office.15%29.aspx) <br/> |[Trigger_Type](trigger_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Del  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type.  <br/> |
|IX  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type.  <br/> |
|LocalName  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
|N  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
|T  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type.  <br/> |
   

