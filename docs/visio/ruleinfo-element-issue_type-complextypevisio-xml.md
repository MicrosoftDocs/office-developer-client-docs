---
title: "RuleInfo element (Issue_Type complexType) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: aec47b43-adbe-3344-fbac-29554f244c99
description: "Specifies information about the validation rule that the parent validation issue pertains to."
---

# RuleInfo element (Issue_Type complexType) (Visio XML)

Specifies information about the validation rule that the parent validation issue pertains to.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[RuleInfo_Type](ruleinfo_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="RuleInfo" type="RuleInfo_Type" minOccurs="0" maxOccurs="1" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Issue](issue-element-issues_type-complextypevisio-xml.md) <br/> |[Issue_Type](issue_type-complextypevisio-xml.md) <br/> |Represents a single validation issue in the document. |
   
### Child elements

None.
  
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|RuleID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the unique identifier of the validation rule that the parent issue pertains to. |Values of the xsd:unsignedInt type. |
|RuleSetID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the unique identifier of the validation rule set that the parent issue pertains to. |Values of the xsd:unsignedInt type. |
   

