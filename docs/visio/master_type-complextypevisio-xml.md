---
title: "Master_Type complexType (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 2d799074-13d9-3c98-3bee-b57af9966c81

---

# Master_Type complexType (Visio XML)

## Type information

||Value |
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
          <xs:complexType name="Master_Type">
          
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
    
    <xs:element name="Icon"  type="Icon_Type"
     minOccurs="0"
     maxOccurs="1"
    >
    </xs:element>
    
      </xs:all>
    <xs:attribute name="ID"
  type="xsd:unsignedInt"
     use="required"
    />
    <xs:attribute name="BaseID"
  type="xsd:string"
    />
    <xs:attribute name="UniqueID"
  type="xsd:string"
    />
    <xs:attribute name="MatchByName"
  type="xsd:boolean"
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
    <xs:attribute name="IconSize"
  type="xsd:unsignedShort"
    />
    <xs:attribute name="PatternFlags"
  type="xsd:unsignedShort"
    />
    <xs:attribute name="Prompt"
  type="xsd:string"
    />
    <xs:attribute name="Hidden"
  type="xsd:boolean"
    />
    <xs:attribute name="IconUpdate"
  type="xsd:boolean"
    />
    <xs:attribute name="AlignName"
  type="xsd:unsignedShort"
    />
    <xs:attribute name="MasterType"
  type="xsd:unsignedShort"
    />
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Icon](icon-element-master_type-complextypevisio-xml.md) <br/> |[Icon_Type](icon_type-complextypevisio-xml.md) <br/> ||
|[PageSheet](pagesheet-element-master_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> ||
|[Rel](rel-element-master_type-complextypevisio-xml.md) <br/> |[Rel_Type](rel_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|AlignName  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type. |
|BaseID  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|Hidden  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|IconSize  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type. |
|IconUpdate  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> ||Values of the xsd:unsignedInt type. |
|IsCustomName  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|IsCustomNameU  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|MasterType  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type. |
|MatchByName  <br/> |xsd:boolean  <br/> |optional  <br/> ||Values of the xsd:boolean type. |
|Name  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|NameU  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|PatternFlags  <br/> |xsd:unsignedShort  <br/> |optional  <br/> ||Values of the xsd:unsignedShort type. |
|Prompt  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
|UniqueID  <br/> |xsd:string  <br/> |optional  <br/> ||Values of the xsd:string type. |
   

