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

|||
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
|[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |[ShapeSheet_Type](shapesheet_type-complextypevisio-xml.md) <br/> |Specifies cell elements that provide information for the definition of a shape.  <br/> |
|[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |[DocumentSheet_Type](documentsheet_type-complextypevisio-xml.md) <br/> |Defines the DocumentSheet structure.  <br/> |
|[StyleSheet](stylesheet-element-stylesheets_type-complextypevisio-xml.md) <br/> |[StyleSheet_Type](stylesheets_type-complextypevisio-xml.md) <br/> |Represents a style defined in a document.  <br/> |
|[PageSheet (Master_Type complexType)](pagesheet-element-master_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |Specifies the properties of the drawing page associated with the master.  <br/> |
|[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |[PageSheet_Type](pagesheet_type-complextypevisio-xml.md) <br/> |Specifies the properties of the drawing page associated with the drawing page.  <br/> |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-trigger_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference toa page in the drawing.  <br/> |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|N  <br/> |xsd:string  <br/> |required  <br/> |The name of the formula to be called when the trigger is activated.  <br/> See the Remarks section.  <br/> |Values of the xsd:string type.  <br/> |
   
## Remarks

The **N** attribute of this **Trigger** element must be one of a limited set of values that correspond to trigger instructions. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Trigger** element. 
  
|**Value**|**Parent element**|**Description**|
|:-----|:-----|:-----|
|CategoryChanged  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **HASCATEGORIES** function exists.  <br/> |
|RecalcBkgPageName  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **BKGPAGENAME** function exists  <br/> |
|RecalcColor  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page whenever the page or any of its contained shapes uses a **RGB** function.  <br/> |
|RecalcCreateDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCCREATION** function exists.  <br/> |
|RecalcData1  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **DATA1** function exists.  <br/> |
|RecalcData2  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **DATA2** function exists.  <br/> |
|RecalcData3  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **DATA3** function exists.  <br/> |
|RecalcEditDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCLASTEDIT** function exists.  <br/> |
|RecalcID  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **ID** function exists.  <br/> |
|RecalcMasterName  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **MASTERNAME** function exists.  <br/> |
|RecalcName  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **NAME** function exists.  <br/> |
|RecalcNowAndRand  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page if either the page or any of its containing shapes have a **NOW** or a **RAND** function.  <br/> |
|RecalcPageCount  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **PAGECOUNT** function exists.  <br/> |
|RecalcPageName  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> [Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **PAGENAME** function exists.  <br/> |
|RecalcPageNum  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **PAGENUMBER** function exists.  <br/> |
|RecalcPath  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **POINTALONGPATH**, **PATHLENGTH**, or **PATHSEGMENT** function exists.  <br/> |
|RecalcPrintDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCLASTPRINT** function exists.  <br/> |
|RecalcSaveDT  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **DOCLASTSAVE** function exists.  <br/> |
|RecalcSummary  <br/> |[DocumentSheet](documentsheet-element-visiodocument_type-complextypevisio-xml.md) <br/> |A trigger that appears on a document when a cross-part reference using a **CATEGORY**, **CREATOR**, **DESCRIPTION**, **KEYWORDS**, **SUBJECT**, or **TITLE** function exists.  <br/> |
|RecalcType  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **TYPE** function exists.  <br/> |
|RelChanged  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a shape when a cross-part reference using a **CONTAINERMEMBERCOUNT** function exists.  <br/> |
|ZOrderChanged  <br/> |[PageSheet (Page_Type complexType)](pagesheet-element-page_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **CONTAINERSHEETREF** function exists.  <br/> |
|Path  <br/> |[Shape](shape-element-shapes_type-complextypevisio-xml.md) <br/> |A trigger that appears on a page when a cross-part reference using a **POINTALONGPATH**, **PATHLENGTH**, or **PATHSEGMENT** function exists.  <br/> |
   

