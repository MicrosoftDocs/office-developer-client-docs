---
title: "Trigger element (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: d897d2d1-25ba-48d7-b87e-d3c533d88c15
description: "Provides instructions to Microsoft Visio to recalculate a relationship between document parts in a Visio file."
---

# Trigger element (Visio XML)

Provides instructions to Microsoft Visio to recalculate a relationship between document parts in a Visio file.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Trigger_Type](trigger_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |master#.xml, page#.xml  <br/> |
   
## Definition

```XML
<xs:element name="Trigger" type="Trigger_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element>
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |[ShapeSheet_Type](shapesheet_type-complextypevisio-xml.md) <br/> |Specifies cell elements that provide information for the definition of a shape. |
|[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |[DocumentSheet_Type](documentsheet_type-complextypevisio-xml.md) <br/> |Defines the DocumentSheet structure. |
|[StyleSheet](stylesheet-element-stylesheets_type-complextypevisio-xml.md) <br/> |[StyleSheet_Type](stylesheets_type-complextypevisio-xml.md) <br/> |Represents a style defined in a document. |
|[PageSheet (Master_Type complexType)](pagesheet-element-master_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |Specifies the properties of the drawing page associated with the master. |
|[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |Specifies the properties of the drawing page associated with the drawing page. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-trigger_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference toa page in the drawing. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|N  <br/> |xsd:string  <br/> |required  <br/> |The name of the formula to be called when the trigger is activated. See the Remarks section. |Values of the xsd:string type. |
   
## Remarks

The **N** attribute of this **Trigger** element must be one of a limited set of values that correspond to trigger instructions. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Trigger** element. 
  
|**Value**|**Parent element**|**Description**|
|:-----|:-----|:-----|
|CategoryChanged  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **HASCATEGORIES** function exists. |
|RecalcBkgPageName  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **BKGPAGENAME** function exists  <br/> |
|RecalcColor  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page whenever the page or any of its contained shapes uses a **RGB** function. |
|RecalcCreateDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCCREATION** function exists. |
|RecalcData1  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **DATA1** function exists. |
|RecalcData2  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **DATA2** function exists. |
|RecalcData3  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **DATA3** function exists. |
|RecalcEditDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCLASTEDIT** function exists. |
|RecalcID  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **ID** function exists. |
|RecalcMasterName  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **MASTERNAME** function exists. |
|RecalcName  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **NAME** function exists. |
|RecalcNowAndRand  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page if either the page or any of its containing shapes have a **NOW** or a **RAND** function. |
|RecalcPageCount  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **PAGECOUNT** function exists. |
|RecalcPageName  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> [Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **PAGENAME** function exists. |
|RecalcPageNum  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **PAGENUMBER** function exists. |
|RecalcPath  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **POINTALONGPATH**, **PATHLENGTH**, or **PATHSEGMENT** function exists. |
|RecalcPrintDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCLASTPRINT** function exists. |
|RecalcSaveDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCLASTSAVE** function exists. |
|RecalcSummary  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **CATEGORY**, **CREATOR**, **DESCRIPTION**, **KEYWORDS**, **SUBJECT**, or **TITLE** function exists. |
|RecalcType  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **TYPE** function exists. |
|RelChanged  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **CONTAINERMEMBERCOUNT** function exists. |
|ZOrderChanged  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **CONTAINERSHEETREF** function exists. |
|Path  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **POINTALONGPATH**, **PATHLENGTH**, or **PATHSEGMENT** function exists. |
   

