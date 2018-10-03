---
title: "RuleSet element (RuleSets_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 5ca63b8a-782e-211f-be7a-8e177b61d8fc
description: "Represents one set of diagram-validation rules."
---

# RuleSet element (RuleSets_Type complexType) ('Visio XML')

Represents one set of diagram-validation rules.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[RuleSet_Type](ruleset_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="RuleSet" type="RuleSet_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RuleSets](rulesets-element-validation_type-complextypevisio-xml.md) <br/> |[RuleSets_Type](rulesets_type-complextypevisio-xml.md) <br/> |Includes a **RuleSet** element for each validation rule set in the document.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Rule](rule-element-ruleset_type-complextypevisio-xml.md) <br/> |[Rule_Type](rule_type-complextypevisio-xml.md) <br/> |Represents a single validation rule in a diagram validation rule set.  <br/> |
|[RuleSetFlags](rulesetflags-element-ruleset_type-complextypevisio-xml.md) <br/> |[RuleSetFlags_Type](rulesetflags_type-complextypevisio-xml.md) <br/> |Specifies rule-set properties.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Description  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the description that appears in the user interface for the validation rule set. Default is an empty string.  <br/> |Values of the xsd:string type.  <br/> |
|Enabled  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether the rules in the specified validation rule set are checked when validation is triggered for the current document. Default is True.  <br/> |Values of the xsd:boolean type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the unique identifier of the validation rule set.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Name  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the local name of the validation rule set. Defaults to NameU attribute value.  <br/> |Values of the xsd:string type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |required  <br/> |Specifies the universal name of the validation rule set.  <br/> |Values of the xsd:string type.  <br/> |
   

