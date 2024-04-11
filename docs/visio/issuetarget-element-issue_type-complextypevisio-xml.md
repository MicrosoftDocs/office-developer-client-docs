---
title: "IssueTarget element (Issue_Type complexType) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: bd9a5d5f-16fe-29b4-5af0-913b14d2be16
description: "Depending on the target of the parent validation issue, specifies either the page, or both the page and the shape, associated with the parent validation issue. If the target of the parent validation issue is a document, IssueTarget specifes neither a page nor a shape."
---

# IssueTarget element (Issue_Type complexType) (Visio XML)

Depending on the target of the parent validation issue, specifies either the page, or both the page and the shape, associated with the parent validation issue. If the target of the parent validation issue is a document, **IssueTarget** specifes neither a page nor a shape. 
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[IssueTarget_Type](issuetarget_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |validation.xml  <br/> |
   
## Definition

```XML
< xs:element name="IssueTarget" type="IssueTarget_Type" minOccurs="0" maxOccurs="1" >
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
|PageID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the unique identifier of the page that is associated with the parent validation issue. If the target is the document, the PageID value can be 0xFFFFFFFF. |Values of the xsd:unsignedInt type. |
|ShapeID  <br/> |xsd:unsignedInt  <br/> |required  <br/> |Specifies the unique identifier of the shape that is associated with the parent validation issue. If the target is the document or a page, the ShapeID value can be 0xFFFFFFFF. |Values of the xsd:unsignedInt type. |
   

