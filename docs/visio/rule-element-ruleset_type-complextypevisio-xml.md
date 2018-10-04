---
title: "Rule element (RuleSet_Type complexType) ('Visio XML')"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: fcd22f3a-c8e8-1133-160c-fe26e612a15d
description: "Represents a single validation rule in a diagram validation rule set."
---

# Rule element (RuleSet_Type complexType) ('Visio XML')

Represents a single validation rule in a diagram validation rule set.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Rule_Type](rule_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |https://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="Rule" type="Rule_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RuleSet](ruleset-element-rulesets_type-complextypevisio-xml.md) <br/> |[RuleSet_Type](ruleset_type-complextypevisio-xml.md) <br/> |Represents one set of diagram-validation rules.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RuleFilter](rulefilter-element-rule_type-complextypevisio-xml.md) <br/> |[RuleFilter_Type](rulefilter_type-complextypevisio-xml.md) <br/> |Specifies the logical expression that determines whether the validation rule should be applied to a target object.  <br/> |
|[RuleTest](ruletest-element-rule_type-complextypevisio-xml.md) <br/> |[RuleTest_Type](ruletest_type-complextypevisio-xml.md) <br/> |Specifies the logical expression that determines whether the target object satisfies the validation rule.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|Category  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the text displayed in the **Category** column of the Issues window. Default is an empty string.  <br/> |Values of the xsd:string type.  <br/> |
|Description  <br/> |xsd:string  <br/> |optional  <br/> |Specifies the description of the validation rule that appears in the user interface. Default is "Unknown".  <br/> |Values of the xsd:string type.  <br/> |
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the unique identifier for the validation rule.  <br/> |Values of the xsd:unsignedInt type.  <br/> |
|Ignored  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies whether the validation rule is currently ignored. Default is False.  <br/> |Values of the xsd:boolean type.  <br/> |
|NameU  <br/> |xsd:string  <br/> |required  <br/> |Specifies the universal name of the validation rule.  <br/> |Values of the xsd:string type.  <br/> |
|RuleTarget  <br/> |xsd:int  <br/> |optional  <br/> |Specifies the type of object to which the validation rule applies.  <br/> |Values of the xsd:int type.  <br/> |
   

