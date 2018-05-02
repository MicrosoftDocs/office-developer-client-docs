---
title: "Extensions_Type complexType ('Visio XML')"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 5f516e1a-e789-8085-1cc3-70514910eb26

---

# Extensions_Type complexType ('Visio XML')

## Type information

|||
|:-----|:-----|
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2011/1/core  <br/> |
|**Schema file** <br/> |VisioSchema15-2012-06-05.xsd  <br/> |
|**Extension base** <br/> |None  <br/> |
   
## Definition

```XML
          <xs:complexType name="Extensions_Type">
          
          <xs:sequence>
    <xs:element name="CellDef"  type="CellDef_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
    <xs:element name="FunctionDef"  type="FunctionDef_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
    <xs:element name="SectionDef"  type="SectionDef_Type"
     minOccurs="0"
     maxOccurs="unbounded"
    >
    </xs:element>
    
      </xs:sequence>
      </xs:complexType>
      
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[CellDef](http://msdn.microsoft.com/library/8fb193f0-5c88-6891-1cda-f1df486aabfc%28Office.15%29.aspx) <br/> |[CellDef_Type](celldef_type-complextypevisio-xml.md) <br/> ||
|[FunctionDef](http://msdn.microsoft.com/library/dad99181-c14c-cce7-3883-106fe05f20a6%28Office.15%29.aspx) <br/> |[FunctionDef_Type](functiondef_type-complextypevisio-xml.md) <br/> ||
|[SectionDef](http://msdn.microsoft.com/library/751da480-f387-4c68-6699-8948271c23ac%28Office.15%29.aspx) <br/> |[SectionDef_Type](sectiondef_type-complextypevisio-xml.md) <br/> ||
   
### Attributes

None.
  

