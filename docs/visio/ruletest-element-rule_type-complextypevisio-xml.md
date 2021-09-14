---
title: "RuleTest element (Rule_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 0cb95b34-3ce0-07a5-5d57-8ac9b0570b9a
description: "Specifies the logical expression that determines whether the target object satisfies the validation rule."
---

# RuleTest element (Rule_Type complexType) (Visio XML)

Specifies the logical expression that determines whether the target object satisfies the validation rule.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RuleTest_Type](ruletest_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="RuleTest" type="RuleTest_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Rule](rule-element-ruleset_type-complextypevisio-xml.md) <br/> |[Rule_Type](rule_type-complextypevisio-xml.md) <br/> |Represents a single validation rule in a diagram validation rule set.  <br/> |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Formula  <br/> |xsd:string  <br/> |optional  <br/> |Represents the element's formula.  <br/> |Values of the xsd:string.  <br/> |
   

