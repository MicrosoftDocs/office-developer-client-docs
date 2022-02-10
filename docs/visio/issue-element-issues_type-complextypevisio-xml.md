---
title: "Issue element (Issues_Type complexType) (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 5c4d07bf-4edc-e241-7827-017f96c11957
description: "Represents a single validation issue in the document."
---

# Issue element (Issues_Type complexType) (Visio XML)

Represents a single validation issue in the document.
  
## Element information

|||
|:-----|:-----|
|**Element type** <br/> |[Issue_Type](issue_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="Issue" type="Issue_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Issues](issues-element-validation_type-complextypevisio-xml.md) <br/> |[Issues_Type](issues_type-complextypevisio-xml.md) <br/> |Contains all the **Issue** elements for the document. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[IssueTarget](issuetarget-element-issue_type-complextypevisio-xml.md) <br/> |[IssueTarget_Type](issuetarget_type-complextypevisio-xml.md) <br/> |Depending on the target of the parent validation issue, specifies either the page, or both the page and the shape, associated with the parent validation issue. |
|[RuleInfo](ruleinfo-element-issue_type-complextypevisio-xml.md) <br/> |[RuleInfo_Type](ruleinfo_type-complextypevisio-xml.md) <br/> |Specifies information about the validation rule that the parent validation issue pertains to. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|ID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the unique identifier of the validation issue. |Values of the xsd:unsignedInt type. |
|Ignored  <br/> |xsd:boolean  <br/> |optional  <br/> |Specifies information about the validation rule that the parent validation issue pertains to. |Values of the xsd:boolean type. |
   

