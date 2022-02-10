---
title: "Page_Type complexType (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 4bc5c0c4-3ee3-7f63-541a-1f1854d4201c

---

# Page_Type complexType (Visio XML)

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
          <xs:complexType name="Page_Type">
          
          <xs:all>
    <xs:element name="PageSheet"  type="PageSheet_Type"
     minOccurs="0"
     maxOccurs="1"
    >
    </xs:element>
    
    <xs:element name="Rel"  type="Rel_Type"
     minOccurs="1"
     maxOccurs="1"
    >
    </xs:element>
    
      </xs:all>
    <xs:attribute name="ID"
  type="xsd:unsignedInt"
     use="required"
    />
    <xs:attribute name="Name"
  type="xsd:string"
    />
    <xs:attribute name="NameU"
  type="xsd:string"
    />
    <xs:attribute name="IsCustomName"
  type="xsd:boolean"
    />
    <xs:attribute name="IsCustomNameU"
  type="xsd:boolean"
    />
    <xs:attribute name="Background"
  type="xsd:boolean"
    />
    <xs:attribute name="BackPage"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="ViewScale"
  type="xsd:double"
    />
    <xs:attribute name="ViewCenterX"
  type="xsd:double"
    />
    <xs:attribute name="ViewCenterY"
  type="xsd:double"
    />
    <xs:attribute name="ReviewerID"
  type="xsd:unsignedInt"
    />
    <xs:attribute name="AssociatedPage"
  type="xsd:unsignedInt"
    />
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[PageSheet](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> ||
|[Rel](rel-element-page_type-complextypevisio-xml.md) <br/> |[Rel_Type](rel_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|AssociatedPage  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type. |
|Background  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|BackPage  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type. |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|Name  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|ReviewerID  <br/> |xsd:unsignedInt  <br/> |optional  <br/> ||Values of the xsd:unsignedInt type. |
|ViewCenterX  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type. |
|ViewCenterY  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type. |
|ViewScale  <br/> |xsd:double  <br/> |optional  <br/> ||Values of the xsd:double type. |
   

