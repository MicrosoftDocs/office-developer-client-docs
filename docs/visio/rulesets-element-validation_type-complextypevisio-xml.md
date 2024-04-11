---
title: "RuleSets element (Validation_Type complexType) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 7a0201e6-9a93-83ae-8a0a-47630ed291ce
description: "Includes a RuleSet element for each validation rule set in the document."
---

# RuleSets element (Validation_Type complexType) (Visio XML)

Includes a **RuleSet** element for each validation rule set in the document. 
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[RuleSets_Type](rulesets_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="RuleSets" type="RuleSets_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Validation](validation-elementvisio-xml.md) <br/> |[Validation_Type](validation_type-complextypevisio-xml.md) <br/> |Stores information about diagram validation for the document. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RuleSet](ruleset-element-rulesets_type-complextypevisio-xml.md) <br/> |[RuleSet_Type](ruleset_type-complextypevisio-xml.md) <br/> |Represents one set of diagram-validation rules. |
   
### Attributes

None.
  

