---
title: "New in Visio for developers" 
manager: soliver
ms.date: 09/18/2015
ms.audience: Developer
ms.topic: overview 
ms.localizationpriority: medium
ms.assetid: 7e3fb858-0ab8-bd2e-217c-c85b10d79785
description: "This document provides a top-level view of the enhancements and additions for developers in Visio 2013. For developers who are ready to get a jump start on the Visio platform, it provides you with sufficient detail to begin coding against Visio 2013."
---

# New in Visio for developers

This document provides a top-level view of the enhancements and additions for developers in Visio 2013. For developers who are ready to get a jump start on the Visio platform, it provides you with sufficient detail to begin coding against Visio 2013.
  
## Introduction

<a name="vis15_WhatsNew_Intro"> </a>

Visio 2013 provides a powerful single platform for your custom drawing solutions. New objects, collections, properties, methods, enumerations, and events, along with new ShapeSheet cells and functions, give you more options for defining the behavior of the elements in your solutions.
  
Among the new features of interest to developers in Visio 2013 are the new file format; robust updates to themes; change shape feature (allowing you to replace shapes with another); new shape effects; improvements to commenting; coauthoring on SharePoint Server 2013; customizable image clipping; relative geometry; support for Business Connectivity Services (BCS) data; updates to Visio Services in Microsoft SharePoint Server 2013; and a duplicate page feature. This topic gives a brief summary of each of these features and mentions some of the new Visio objects and members that are associated with the features and exposed in Visual Basic for Applications (VBA). For information about these features and accompanying code samples, see the [Visio Developer Center](https://msdn.microsoft.com/office/aa905478.aspx).
  
> [!NOTE]
> Visio 2013 includes many new ShapeSheet cells, rows, and functions to support the new features in Visio. For more information about what's new in the ShapeSheet for Visio 2013, see the article [What's new for Visio ShapeSheet developers](what-s-new-for-visio-shapesheet-developers.md).
  
## New file format

<a name="vis15_WhatsNew_NewFF"> </a>

Visio 2013 introduces a new file format, based on the Open Packaging Conventions (OPC) standard (ISO 29500, Part 2) and the XML elements from the previous Visio XML file format (.vdx). It is a zipped, XML-based file format similar to the file formats used in other applications.
  
Because the new file format is supported by both Visio 2013 and Visio Services in Microsoft SharePoint Server 2013, you can save a Visio drawing directly to an SharePoint Server library, without having to publish the file as a Visio Web Drawing (.vdw). Even so, Visio Services can still read and display Visio Web Drawing files.
  
The new file format includes the following file types (by extension):
  
- .vsdx (Visio drawing)

- .vsdm (Visio macro-enabled drawing)

- .vssx (Visio stencil)

- .vssm (Visio macro-enabled stencil)

- .vstx (Visio template)

- .vstm (Visio macro-enabled template)

By using existing support for reading and writing to the file format package (such as [System.IO.Packaging](https://msdn.microsoft.com/library/System.IO.Packaging.aspx) ) and for parsing XML ( [System.Xml.Linq](https://msdn.microsoft.com/library/System.Xml.Linq.aspx) ), you can programmatically work with the new file formats.
  
Visio 2013 retains the ability to read the old file formats (.vsd, .vss, .vst, .vdx, .vsx, .vtx, .vdw, .vwi). Visio 2013 does not save to the previous Visio XML file format (.vdx). Solutions or tools that consume the previous Visio XML file format (.vdx) files may need to be refactored in order to read the new file format and its schemas.
  
Visio Services retains the ability to display the Visio Web Drawing (.vdw) format in the browser. It now also renders the new Visio drawing (.vsdx) and Visio macro-enabled drawing (.vsdm) formats.
  
## Themes

<a name="vis15_WhatsNew_Themes"> </a>

Themes have been redesigned in Visio 2013, making use of a greater variety of effects and styles including the integration of Shape Art effects. Users can now decide on an overarching style by applying a theme, personalize the diagram with theme variants, and highlight individual shapes with Quick Styles. ShapeSheet developers can take advantage of these features with new functions and cells in the ShapeSheet.
  
You can also manipulate themes at the [Page](https://msdn.microsoft.com/library/7a7f37ab-b448-eb70-b4f1-c185dfbd511e%28Office.15%29.aspx), [Shape](https://msdn.microsoft.com/library/da7a8872-4ebb-a607-e0ed-eebf68ff5630%28Office.15%29.aspx), and [Selection](https://msdn.microsoft.com/library/e5734140-6dbe-7de8-9695-1a22fb4ac628%28Office.15%29.aspx) object level. New APIs for working with themes include [Page.SetTheme](https://msdn.microsoft.com/library/5a186f58-9a7a-bd8a-826b-85da75a4d59f%28Office.15%29.aspx) method, [Page.SetThemeVariant](https://msdn.microsoft.com/library/8393a95f-83ca-0efa-d987-ae498bfe5e9d%28Office.15%29.aspx) method, [Shape.SetQuickStyle](https://msdn.microsoft.com/library/aebe80cb-fae9-0be7-e903-882f6eb58b63%28Office.15%29.aspx) method, and the [Selection.SetQuickStyle](https://msdn.microsoft.com/library/39b810b5-0738-daed-0103-8a2df07559c6%28Office.15%29.aspx) method.
  
For a detailed list of the new APIs in Visio 2013, see the [Visio object model changes](#vis15_WhatsNew_NewOM) section in this article. For more information about the new ShapeSheet cells in Visio 2013, see the article [What's new for Visio ShapeSheet developers](what-s-new-for-visio-shapesheet-developers.md).
  
## Change shape

<a name="vis15_WhatsNew_ChangeShapes"> </a>

Visio 2013 includes a shape replacement API that enables you to swap one or more shapes for another shape contained in a stencil, while retaining some of the local values from the original shape, like the shape text shape, shape data, or shape formatting. Shape developers can update the ShapeSheet settings of their custom shapes to specify the Change Shape behavior for their shapes. Among the new APIs are the [Shape.ReplaceShapes](https://msdn.microsoft.com/library/b330a63d-4e3f-0c4d-c38c-6ee806670225%28Office.15%29.aspx) and [Selection.ReplaceShapes](https://msdn.microsoft.com/library/dc278901-77ce-e1fe-c44f-f464bbb1c360%28Office.15%29.aspx) methods and the [ReplaceShape](https://msdn.microsoft.com/library/26c4e7cb-6618-6d2f-a4be-515584f8cd10%28Office.15%29.aspx) event.
  
For a detailed list of the new APIs in Visio 2013, see the [Visio object model changes](#vis15_WhatsNew_NewOM) section in this article. For more information about the new ShapeSheet cells in Visio 2013, see the article [What's new for Visio ShapeSheet developers](what-s-new-for-visio-shapesheet-developers.md).
  
## Shape effects

<a name="vis15_WhatsNew_ShapeEffects"> </a>

New shape effects such as bevel, 3-D rotation, glow, reflection, and sketching have been added to Visio 2013. The ShapeSheet includes new cells for working with these affects.
  
For more information about the new ShapeSheet cells in Visio 2013, see the article [What's new for Visio ShapeSheet developers](what-s-new-for-visio-shapesheet-developers.md).
  
## Commenting

<a name="vis15_WhatsNew_Commenting"> </a>

Visio 2013 includes a new commenting framework. Comments can now be associated with a particular shape or page. Visio 2013 includes two new objects, [Comments](https://msdn.microsoft.com/library/f028cc03-0ef1-8017-a936-d30d45211864%28Office.15%29.aspx) and [Comment](https://msdn.microsoft.com/library/7cd0ee53-6b8d-a03b-ecd6-f6f6dda0f2d4%28Office.15%29.aspx). New APIs for accessing comments programmatically include the [Document.Comments](https://msdn.microsoft.com/library/15a322ad-70eb-1487-701d-76e2fde73309%28Office.15%29.aspx), [Page.Comments](https://msdn.microsoft.com/library/9618c86c-96c0-be95-ee20-5d1b99f4d5e8%28Office.15%29.aspx), [Shape.Comments](https://msdn.microsoft.com/library/498eca91-beb9-b764-0262-a935e5205710%28Office.15%29.aspx), and [Page.ShapeComments](https://msdn.microsoft.com/library/b7d86594-ba1f-627b-222f-905da1b1201e%28Office.15%29.aspx) properties.
  
Visio Services includes JavaScript APIs to read the comments from a page or shape in a diagram.
  
For a detailed list of the new APIs in Visio 2013, see the [Visio object model changes](#vis15_WhatsNew_NewOM) section in this article.
  
> [!NOTE]
> Comments are no longer accessible through the ShapeSheet.
  
## Coauthoring

<a name="vis15_WhatsNew_Coauthoring"> </a>

Visio 2013 includes the ability to co-author diagrams stored on SharePoint or Microsoft OneDrive. Developers have access to the [Document.AfterDocumentMerge](https://msdn.microsoft.com/library/50658da5-592a-4d16-908f-c6abe3050f09%28Office.15%29.aspx) event which provides information about diagram changes due to coauthoring. Solution developers also have the ability to disable coauthoring to suit their custom needs using the [NoCoauth](nocoauth-cell-document-properties-section.md) cell on the Document ShapeSheet.
  
For a detailed list of the new APIs in Visio 2013, see the [Visio object model changes](#vis15_WhatsNew_NewOM) section in this article.
  
## Customizable image clipping

<a name="vis15_WhatsNew_ClipImages"> </a>

Visio 2013 supports defining a Custom Image Clipping path to crop images to any shape. This extends the capacities of Visio 2010, which supported clipping images in a rectangular way. This functionality is available in the ShapeSheet by using the [ClippingPath](clippingpath-cell-foreign-image-info-section.md) cell in the **Foreign Image Info** section.
  
For more information about the new ShapeSheet cells in Visio 2013, see the article [What's new for Visio ShapeSheet developers](what-s-new-for-visio-shapesheet-developers.md).
  
## Relative geometries

<a name="vis15_WhatsNew_RelativeGeometry"> </a>

In previous versions of Visio, shape geometry was defined by formulas that depended on the height or width of the shape. For example, in Visio 2010 the vertices of many built-in Visio shapes were defined by multiplying the height or width of the shape by a constant. These shapes had **Geometry** sections that included [MoveTo](moveto-row-geometry-section.md) or [LineTo](lineto-row-geometry-section.md) rows (for example) with formulas like `Width*1` and `Height*0`.
  
Visio 2013 now supports relative geometry in the ShapeSheet. Shape developers can now use relative geometries to specify geometries as simple values or formulas, which multiply by the height or width automatically. Shape vertices can now be expressed with constants, for instance, removing the need to express vertices as multiples of the shape width or height. This makes it easier for developers to create shapes, with better performance and smaller file sizes. New rows include the [RelMoveTo](relmoveto-row-geometry-section.md) and [RelLineTo](rellineto-row-geometry-section.md) rows where the **X** and **Y** cell values are automatically multiplied by the width or height of the shape (respectively).
  
For more information about the new ShapeSheet rows in Visio 2013, see the article [What's new for Visio ShapeSheet developers](what-s-new-for-visio-shapesheet-developers.md).
  
## Support for Business Connectivity Services (BCS) data

<a name="vis15_WhatsNew_BCS"> </a>

Visio 2013 diagrams can now be connected to external lists on SharePoint Server 2013 servers. An external list is a content source external to SharePoint (for example, a SQL Server table) that has been connected to a SharePoint list by using Microsoft Business Connectivity Services (BCS). Visio Services supports the ability to refresh the Visio diagrams as the data updates.
  
For more information about what's new in Visio Services, see the article [Visio Services in SharePoint 2013](https://msdn.microsoft.com/library/jj164027%28office.15%29.aspx). For more information about Business Connectivity Services (BCS), see [Business Connectivity Services in SharePoint 2013](https://msdn.microsoft.com/library/jj163782%28office.15%29.aspx).
  
## Improvements in Visio Services

<a name="vis15_WhatsNew_VisioServices"> </a>

Visio Services in Microsoft SharePoint Server 2013 includes many improvements. As mentioned previously, Visio Services supports the new Visio file format (both .vsdx and .vsdm). Visio Services has expanded data refresh and recalculation, including the ability to recalculate formulas across an entire diagram.
  
For more information about what's new in Visio Services, see the article [Visio Services in SharePoint 2013](https://msdn.microsoft.com/library/jj164027%28office.15%29.aspx).
  
## Duplicate page

<a name="vis15_WhatsNew_DuplicatePage"> </a>

You can now copy a page and all of its shapes within the same document in Visio 2013. Accordingly, the **Page** object has a new method, [Duplicate](https://msdn.microsoft.com/library/394be23b-997d-0da1-b3bd-8278564fb4e0%28Office.15%29.aspx), which duplicates the page and returns a new **Page** object.
  
## Visio object model changes

<a name="vis15_WhatsNew_NewOM"> </a>

New objects, properties, methods, and events have been added to the Visio object model to provide programmability support for new Visio 2013 features. Additionally, object model improvements address frequent developer requests for changes to the Visio platform.
  
### New members

The following members have been added to existing objects in the Visio object model.
  
 **Table 1. Visio object model enhancements**
  
|**Object or collection**|**New members**|
|:-----|:-----|
|[Application Object (Visio)](https://msdn.microsoft.com/library/5b3c8939-793f-116f-11b8-1d4170d95a63%28Office.15%29.aspx) <br/> |[Application.AfterReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/b02de031-086a-41cc-d832-5434b8096444%28Office.15%29.aspx) <br/> |
||[Application.BeforeReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/fbf44569-0539-9292-ce20-1f9e34238b33%28Office.15%29.aspx) <br/> |
||[Application.QueryCancelReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/50c0f2a6-f534-f3af-7e83-c865abda8bf9%28Office.15%29.aspx) <br/> |
||[Application.ReplaceShapesCanceled Event (Visio)](https://msdn.microsoft.com/library/e8eecd64-e4bd-d2c4-b942-c5ff607a4121%28Office.15%29.aspx) <br/> |
|[ApplicationSettings Object (Visio)](https://msdn.microsoft.com/library/f2e24211-ecc6-e0f5-4c00-fc50f98a3505%28Office.15%29.aspx) <br/> |[ApplicationSettings.EnterCommitsText Property (Visio)](https://msdn.microsoft.com/library/ba9ce9fa-d224-cdc3-668d-46c1849911c7%28Office.15%29.aspx) <br/> |
||[ApplicationSettings.SVGExportFormat Property (Visio)](https://msdn.microsoft.com/library/9e7ca1cb-5ace-b75b-0e59-61566b9a0169%28Office.15%29.aspx) <br/> |
|[Document Object (Visio)](https://msdn.microsoft.com/library/21640062-13a2-a2b2-7c61-7e707671207c%28Office.15%29.aspx) <br/> |[Document.AfterDocumentMerge Event (Visio)](https://msdn.microsoft.com/library/50658da5-592a-4d16-908f-c6abe3050f09%28Office.15%29.aspx) <br/> |
||[Document.Comments Property (Visio)](https://msdn.microsoft.com/library/15a322ad-70eb-1487-701d-76e2fde73309%28Office.15%29.aspx) <br/> |
||[Document.CompatibilityMode Property (Visio)](https://msdn.microsoft.com/library/98fc00d3-5d2b-218e-9828-b5581ee7313d%28Office.15%29.aspx) <br/> |
|[Documents Object (Visio)](https://msdn.microsoft.com/library/e9291149-964e-c6fb-4c62-bf2f35a6a0a7%28Office.15%29.aspx) <br/> |[Documents.AfterDocumentMerge Event (Visio)](https://msdn.microsoft.com/library/cac0544d-77b9-b722-cfdb-e42475ce2558%28Office.15%29.aspx) <br/> |
||[Documents.AfterReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/e01c069e-440b-7b8b-8d7d-cdb664f6e2d6%28Office.15%29.aspx) <br/> |
||[Documents.BeforeReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/55a66c47-a2ca-5c8a-2693-aaa1b079c704%28Office.15%29.aspx) <br/> |
||[Documents.QueryCancelReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/d613730e-04c8-d17f-0ad1-19e976aa107d%28Office.15%29.aspx) <br/> |
||[Documents.ReplaceShapesCanceled Event (Visio)](https://msdn.microsoft.com/library/94a20fe7-da09-4e3c-d048-05ba0b8f1070%28Office.15%29.aspx) <br/> |
|[InvisibleApp Object (Visio)](https://msdn.microsoft.com/library/70a30571-2017-af8b-eaa1-bf93c758a46a%28Office.15%29.aspx) <br/> |[InvisibleApp.AfterReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/5d7b8ec2-ef65-1a49-fb50-3fae95d56761%28Office.15%29.aspx) <br/> |
||[InvisibleApp.BeforeReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/bd0e37ca-887a-4d53-3b0c-3339492df3dd%28Office.15%29.aspx) <br/> |
||[InvisibleApp.QueryCancelReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/5e5d9b76-dfd4-1d02-d205-9e64350449d5%28Office.15%29.aspx) <br/> |
||[InvisibleApp.ReplaceShapesCanceled Event (Visio)](https://msdn.microsoft.com/library/17e43497-c7a8-8546-595c-4630afb301a3%28Office.15%29.aspx) <br/> |
|[Page Object (Visio)](https://msdn.microsoft.com/library/7a7f37ab-b448-eb70-b4f1-c185dfbd511e%28Office.15%29.aspx) <br/> |[Page.AfterReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/e4005987-acb1-78d7-91fb-c3c2d5b036e3%28Office.15%29.aspx) <br/> |
||[Page.BeforeReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/57ea9836-74dd-77c2-6541-f8f61b89c0b6%28Office.15%29.aspx) <br/> |
||[Page.Comments Property (Visio)](https://msdn.microsoft.com/library/9618c86c-96c0-be95-ee20-5d1b99f4d5e8%28Office.15%29.aspx) <br/> |
||[Page.Duplicate Method (Visio)](https://msdn.microsoft.com/library/394be23b-997d-0da1-b3bd-8278564fb4e0%28Office.15%29.aspx) <br/> |
||[Page.GetTheme Method (Visio)](https://msdn.microsoft.com/library/31c84e69-0bc8-2d1a-84d8-7397110d74ae%28Office.15%29.aspx) <br/> |
||[Page.GetThemeVariant Method (Visio)](https://msdn.microsoft.com/library/40c2be31-fdb0-68ee-a129-2788b1b17c82%28Office.15%29.aspx) <br/> |
||[Page.QueryCancelReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/17ead23f-825a-c608-3315-e2eed6784cd5%28Office.15%29.aspx) <br/> |
||[Page.ReplaceShapesCanceled Event (Visio)](https://msdn.microsoft.com/library/867b1fc1-96bd-cbeb-fd61-b02a96e039ca%28Office.15%29.aspx) <br/> |
||[Page.SetTheme Method (Visio)](https://msdn.microsoft.com/library/5a186f58-9a7a-bd8a-826b-85da75a4d59f%28Office.15%29.aspx) <br/> |
||[Page.SetThemeVariant Method (Visio)](https://msdn.microsoft.com/library/8393a95f-83ca-0efa-d987-ae498bfe5e9d%28Office.15%29.aspx) <br/> |
||[Page.ShapeComments Property (Visio)](https://msdn.microsoft.com/library/b7d86594-ba1f-627b-222f-905da1b1201e%28Office.15%29.aspx) <br/> |
|[Pages Object (Visio)](https://msdn.microsoft.com/library/45eec568-b5cc-5e80-ff5c-4dfa567efb5d%28Office.15%29.aspx) <br/> |[Pages.AfterReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/05c33bdd-e697-d36e-46a8-45705e9ad2c2%28Office.15%29.aspx) <br/> |
||[Pages.BeforeReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/3f6dbc31-0583-dd67-0432-335d6df7a50c%28Office.15%29.aspx) <br/> |
||[Pages.QueryCancelReplaceShapes Event (Visio)](https://msdn.microsoft.com/library/d11ff976-0016-da6b-92fb-379baa7e8f94%28Office.15%29.aspx) <br/> |
||[Pages.ReplaceShapesCanceled Event (Visio)](https://msdn.microsoft.com/library/f0ce8c66-7a15-5f91-8c89-e177bc6671d2%28Office.15%29.aspx) <br/> |
|[Selection Object (Visio)](https://msdn.microsoft.com/library/e5734140-6dbe-7de8-9695-1a22fb4ac628%28Office.15%29.aspx) <br/> |[Selection.ReplaceShape Method (Visio)](https://msdn.microsoft.com/library/dc278901-77ce-e1fe-c44f-f464bbb1c360%28Office.15%29.aspx) <br/> |
||[Selection.SetQuickStyle Method (Visio)](https://msdn.microsoft.com/library/39b810b5-0738-daed-0103-8a2df07559c6%28Office.15%29.aspx) <br/> |
|[Shape Object (Visio)](https://msdn.microsoft.com/library/da7a8872-4ebb-a607-e0ed-eebf68ff5630%28Office.15%29.aspx) <br/> |[Shape.ChangePicture Method (Visio)](https://msdn.microsoft.com/library/9193d802-cebd-2bfd-5f8e-400fac36c1a5%28Office.15%29.aspx) <br/> |
||[Shape.Comments Property (Visio)](https://msdn.microsoft.com/library/498eca91-beb9-b764-0262-a935e5205710%28Office.15%29.aspx) <br/> |
||[Shape.ReplaceShape Method (Visio)](https://msdn.microsoft.com/library/b330a63d-4e3f-0c4d-c38c-6ee806670225%28Office.15%29.aspx) <br/> |
||[Shape.SetQuickStyle Method (Visio)](https://msdn.microsoft.com/library/aebe80cb-fae9-0be7-e903-882f6eb58b63%28Office.15%29.aspx) <br/> |

### New objects and enumerations

The following objects have been added to the Visio object model.
  
 **Table 2. Visio object model additions**
  
|**Object**|**Properties**|**Methods**|
|:-----|:-----|:-----|
|[CoauthMergeEvent Object (Visio)](https://msdn.microsoft.com/library/eb9425cb-0108-4909-e334-9cd51e5b9303%28Office.15%29.aspx) <br/> |[CoauthMergeEvent.BaseDocument Property (Visio)](https://msdn.microsoft.com/library/7ec09a85-6f51-685b-0c87-4b9eb3266773%28Office.15%29.aspx) <br/> [CoauthMergeEvent.DownloadDocument Property (Visio)](https://msdn.microsoft.com/library/19239540-cd5a-13ea-3b26-282ac3676abd%28Office.15%29.aspx) <br/> [CoauthMergeEvent.ObjectType Property (Visio)](https://msdn.microsoft.com/library/01baa0c2-75b7-2713-9732-1e7a8a7b33aa%28Office.15%29.aspx) <br/> [CoauthMergeEvent.Stat Property (Visio)](https://msdn.microsoft.com/library/d8a96b8e-36b5-c61f-8cea-76266f7eed39%28Office.15%29.aspx) <br/> [CoauthMergeEvent.WorkingDocument Property (Visio)](https://msdn.microsoft.com/library/0f3c4358-0d63-df7f-12fe-7f378bacca86%28Office.15%29.aspx) <br/> |None  <br/> |
|[Comment Object (Visio)](https://msdn.microsoft.com/library/f028cc03-0ef1-8017-a936-d30d45211864%28Office.15%29.aspx) <br/> |[Comment.AssociatedObject Property (Visio)](https://msdn.microsoft.com/library/e28eed2e-260e-59c9-9b24-631817fe1ae1%28Office.15%29.aspx) <br/> [Comment.AuthorInitials Property (Visio)](https://msdn.microsoft.com/library/abc07100-8c5c-9982-674d-40b58c096816%28Office.15%29.aspx) <br/> [Comment.AuthorName Property (Visio)](https://msdn.microsoft.com/library/e1da4db8-7a16-16bf-2a5f-be1ac5372d34%28Office.15%29.aspx) <br/> [Comment.AuthorSipAddress Property (Visio)](https://msdn.microsoft.com/library/f8d185a9-91b6-471a-3c0e-ffa8a06b36b3%28Office.15%29.aspx) <br/> [Comment.AuthorSMTPAddress Property (Visio)](https://msdn.microsoft.com/library/22e04ccc-c524-ca08-d5e2-db68fdb3afb6%28Office.15%29.aspx) <br/> [Comment.Collapsed Property (Visio)](https://msdn.microsoft.com/library/9552e379-e351-78d7-e0ed-4f524c3273a1%28Office.15%29.aspx) <br/> [Comment.CreateDate Property (Visio)](https://msdn.microsoft.com/library/b643e13e-da12-a992-3a59-99b37f003fb9%28Office.15%29.aspx) <br/> [Comment.Document Property (Visio)](https://msdn.microsoft.com/library/d57b1377-b895-1fe1-2f98-ef000fdd9c39%28Office.15%29.aspx) <br/> [Comment.EditDate Property (Visio)](https://msdn.microsoft.com/library/4ad13f54-215e-3680-5de6-13715e309fbf%28Office.15%29.aspx) <br/> [Comment.ObjectType Property (Visio)](https://msdn.microsoft.com/library/bf0d786d-e1b6-65f1-3112-5dfd4ff324e9%28Office.15%29.aspx) <br/> [Comment.Stat Property (Visio)](https://msdn.microsoft.com/library/f457598c-af42-cb83-ecd2-4fd42898ea16%28Office.15%29.aspx) <br/> [Comment.Text Property (Visio)](https://msdn.microsoft.com/library/3ec63034-de5f-d9f2-16a5-e06a56883867%28Office.15%29.aspx) <br/> |[Comment.Delete Method (Visio)](https://msdn.microsoft.com/library/7762f264-f680-5758-7c35-dfe9067b61ca%28Office.15%29.aspx) <br/> |
|[Comments Object (Visio)](https://msdn.microsoft.com/library/7cd0ee53-6b8d-a03b-ecd6-f6f6dda0f2d4%28Office.15%29.aspx) <br/> |[Comments.Count Property (Visio)](https://msdn.microsoft.com/library/abac02d5-5047-2c9d-5c5c-e2738f99a4a6%28Office.15%29.aspx) <br/> [Comments.Document Property (Visio)](https://msdn.microsoft.com/library/507d4698-e282-f8a9-1299-c67945ee5fc4%28Office.15%29.aspx) <br/> [Comments.Item Property (Visio)](https://msdn.microsoft.com/library/fed2a079-de87-d5ce-1d74-0bfa5a328441%28Office.15%29.aspx) <br/> [Comments.ObjectType Property (Visio)](https://msdn.microsoft.com/library/06544d73-ce00-2c89-1ecb-20541b251d57%28Office.15%29.aspx) <br/> [Comments.Stat Property (Visio)](https://msdn.microsoft.com/library/1f5f29b2-236c-91b6-6d25-7bacc37ca96c%28Office.15%29.aspx) <br/> |[Comments.Add Method (Visio)](https://msdn.microsoft.com/library/da02de49-8057-7e5c-6b59-0a013e56256d%28Office.15%29.aspx) <br/> [Comments.DeleteAll Method (Visio)](https://msdn.microsoft.com/library/50777ed3-553c-90ae-2d30-9dde412fe6b9%28Office.15%29.aspx) <br/> |
|[ReplaceShapesEvent Object (Visio)](https://msdn.microsoft.com/library/26c4e7cb-6618-6d2f-a4be-515584f8cd10%28Office.15%29.aspx) <br/> |[ReplaceShapesEvent.ObjectType Property (Visio)](https://msdn.microsoft.com/library/bcc442f0-aa4e-cd5a-d116-f3fb74459927%28Office.15%29.aspx) <br/> [ReplaceShapesEvent.ReplaceFlags Property (Visio)](https://msdn.microsoft.com/library/d0d00891-c794-bd0c-d37e-1ab98c92beab%28Office.15%29.aspx) <br/> [ReplaceShapesEvent.ReplacementMaster Property (Visio)](https://msdn.microsoft.com/library/326a1889-8952-b4ac-c5c0-ac4470257c06%28Office.15%29.aspx) <br/> [ReplaceShapesEvent.SelectionSource Property (Visio)](https://msdn.microsoft.com/library/f81c0b66-b63b-fc7c-1769-d56a17d5cf78%28Office.15%29.aspx) <br/> [ReplaceShapesEvent.Stat Property (Visio)](https://msdn.microsoft.com/library/96f3d382-5dda-7f93-088d-96edc831cd7c%28Office.15%29.aspx) <br/> |None  <br/> |

The following table lists the new enumerations and constants introduced in Visio 2013.
  
 **Table 3. Visio enumeration additions**
  
|**Enumeration**|**Description**|
|:-----|:-----|
|[VisQuickStyleColors Enumeration (Visio)](https://msdn.microsoft.com/library/c19d91f3-a9a4-e31e-ed7a-eef15553fbf4%28Office.15%29.aspx) <br/> |Specifies designated names for colors contained within a theme. |
|[VisQuickStyleMatrixIndices Enumeration (Visio)](https://msdn.microsoft.com/library/0fb0b448-85ba-4fc4-d933-21d574cefa2a%28Office.15%29.aspx) <br/> |Specifies designated names for the themes and variations provided with Visio 2013. |
|[VisReplaceFlags Enumeration (Visio)](https://msdn.microsoft.com/library/cf270178-f939-7eb4-b8e1-3b4153aff221%28Office.15%29.aspx) <br/> |Specifies behaviors for a Change Shape operation. |
|[VisSVGExportFormat Enumeration (Visio)](https://msdn.microsoft.com/library/d8ca8c3f-41d9-4e9d-8f6d-f5567361b14e%28Office.15%29.aspx) <br/> |Specifies the inclusion or exclusion of Visio markup when exporting a diagram to SVG. |

### Deprecated objects and members

The following table lists the deprecated objects and members introduced in Visio 2013. Only deprecated object members are listed in the **Deprecated members** column.
  
 **Table 4. Visio object model deprecations**
  
|**Object or collection**|**Deprecated members**|
|:-----|:-----|
|**Window** object  <br/> |**PageTabWidth** property  <br/> |

## See also

<a name="vis15_WhatsNew_Additional"> </a>

- [Visio for developers](https://msdn.microsoft.com/office/aa905478.aspx)
- [What's new for Visio ShapeSheet developers](what-s-new-for-visio-shapesheet-developers.md)
- [Visio Services in SharePoint 2013](https://msdn.microsoft.com/library/jj164027%28office.15%29.aspx)
- [What's new in Visio (Office.com)](https://office.com/redir/HA102749364.aspx)
- [Visio Developer Center](https://msdn.microsoft.com/office/aa905478.aspx)
