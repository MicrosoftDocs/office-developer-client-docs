---
title: "Cell element (Visio XML)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 3131bfbb-9bf6-d15d-c6ca-2f15bd038f39
description: "Specifies cell elements that can be contained within a DocumentSheet, StyleSheet, PageSheet, or ShapeSheet."
---

# Cell element (Visio XML)

Specifies cell elements that can be contained within a DocumentSheet, StyleSheet, PageSheet, or ShapeSheet.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |document.xml, pages.xml, masters.xml, master#.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Cell"  type="Cell_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

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
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference to a drawing page. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|E  <br/> |xsd:string  <br/> |optional  <br/> |Indicates that the formula evaluates to an error. The value of **E** is the current value (an error message string); the value of the **V** attribute is the last valid value. |An error message string. |
|F  <br/> |xsd:string  <br/> |optional  <br/> | Represents the element's formula. This attribute can contain one of the following strings:  <br/>  '(some formula)' if the formula exists locally  <br/> `No Formula` if the formula is locally deleted or blocked  <br/> `Inh` if the formula is inherited. |A formula. |
|N  <br/> |xsd:string  <br/> |required  <br/> |Represents the name of the **ShapeSheet** cell. |The name of the **ShapeSheet** cell. See the Remarks section below. |
|U  <br/> |xsd:string  <br/> |optional  <br/> |Represents a unit of measure The default is DL. |The units of the cell. |
|V  <br/> |xsd:string  <br/> |optional  <br/> |Represents the value of the cell. |The value of the **ShapeSheet** cell. |
   
## Remarks

The **N** attribute of this **Cell** element must be one of a limited set of values that correspond to ShapeSheet cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Cell** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|AddMarkup  <br/> |Indicates whether the document is being reviewed for markup. |[AddMarkup Cell (Document Properties Section)](addmarkup-cell-document-properties-section.md) <br/> |
|AlignBottom  <br/> |Determines the vertical position, relative to the origin of its parent, of a horizontal guide or guide point to which the shape's bottom border is aligned. |[AlignBottom Cell (Alignment Section)](alignbottom-cell-alignment-section.md) <br/> |
|AlignCenter  <br/> |Determines the horizontal position, relative to the origin of its parent, of a vertical guide or guide point to which the shape's horizontal center is aligned. |[AlignCenter Cell (Alignment Section)](aligncenter-cell-alignment-section.md) <br/> |
|AlignLeft  <br/> |Determines the horizontal position, relative to the origin of its parent, of a vertical guide or guide point to which the shape's left border is aligned. |[AlignLeft Cell (Alignment Section)](alignleft-cell-alignment-section.md) <br/> |
|AlignMiddle  <br/> |Determines the vertical position, relative to the origin of its parent, of a horizontal guide or guide point to which the shape's vertical center is aligned. |[AlignMiddle Cell (Alignment Section)](alignmiddle-cell-alignment-section.md) <br/> |
|AlignRight  <br/> |Determines the horizontal position, relative to the origin of its parent, of a vertical guide or guide point to which the shape's right border is aligned. |[AlignRight Cell (Alignment Section)](alignright-cell-alignment-section.md) <br/> |
|AlignTop  <br/> |Determines the vertical position, relative to the origin of its parent, of a horizontal guide or guide point to which the shape's top border is aligned. |[AlignTop Cell (Alignment Section)](aligntop-cell-alignment-section.md) <br/> |
|Angle  <br/> |Represents the shape's current angle of rotation in relation to its parent. The default formula for determining the rotation angle of a 1-D shape is: =ATAN2(EndY-BeginY,EndX-BeginX). |[Angle Cell (Shape Transform Section)](angle-cell-shape-transform-section.md) <br/> |
|AvenueSizeX  <br/> |Determines the amount of horizontal space between shapes on the drawing page when you lay out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). |[AvenueSizeX Cell (Page Layout Section)](avenuesizex-cell-page-layout-section.md) <br/> |
|AvenueSizeY  <br/> |Determines the amount of vertical space between shapes on the drawing page when you lay out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). Determines the amount of vertical space between shapes on the drawing page when you lay out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). |[AvenueSizeY Cell (Page Layout Section)](avenuesizey-cell-page-layout-section.md) <br/> |
|AvoidPageBreaks  <br/> |Determines whether shapes can be placed over page breaks when the shapes are incrementally aligned, incrementally spaced, or both. |[AvoidPageBreaks Cell (Page Layout Section)](avoidpagebreaks-cell-page-layout-section.md) <br/> |
|BeginArrow  <br/> |Indicates whether a line has an arrowhead or other line end format at its first vertex. Enter a number from 0 to 45 or the USE function with the name of a custom line end, or use the Line dialog box. |[BeginArrow Cell (Line Format Section)](beginarrow-cell-line-format-section.md) <br/> |
|BeginArrowSize  <br/> |Determines the size of the arrowhead at the beginning of the line. |[BeginArrowSize Cell (Line Format Section)](beginarrowsize-cell-line-format-section.md) <br/> |
|BeginX  <br/> |Represents the x-coordinate of the begin point of the 1-D shape, in relation to the origin of its parent. Represents the x-coordinate of the begin point of the 1-D shape, in relation to the origin of its parent. |[BeginX Cell (1-D Endpoints Section)](beginx-cell-1-d-endpoints-section.md) <br/> |
|BeginY  <br/> |Represents the y-coordinate of the begin point of the 1-D shape, in relation to the origin of its parent. |[BeginY Cell (1-D Endpoints Section)](beginy-cell-1-d-endpoints-section.md) <br/> |
|BegTrigger  <br/> |Contains a trigger formula generated by the application that determines whether to move the begin point of a 1-D shape to maintain its connection to another shape. |[BegTrigger Cell (Glue Info Section)](begtrigger-cell-glue-info-section.md) <br/> |
|BevelBottomHeight  <br/> |Determines the height of a shape's bottom bevel in points. |[BevelBottomHeight Cell (Bevel Properties Section)](bevelbottomheight-cell-bevel-properties-section.md) <br/> |
|BevelBottomType  <br/> |Specifies the bottom bevel type of a shape's bevel. |[BevelBottomType Cell (Bevel Properties Section)](bevelbottomtype-cell-bevel-properties-section.md) <br/> |
|BevelBottomWidth  <br/> |Determines the width of the bottom bevel in points. |[BevelBottomWidth Cell (Bevel Properties Section)](bevelbottomwidth-cell-bevel-properties-section.md) <br/> |
|BevelContourColor  <br/> |Determines the color of the bevel's contour in RGB value or as determined by the active theme. |[BevelContourColor Cell (Bevel Properties Section)](bevelcontourcolor-cell-bevel-properties-section.md) <br/> |
|BevelContourSize  <br/> |Determines the size of the bevel's contour in points. |[BevelContourSize Cell (Bevel Properties Section)](bevelcontoursize-cell-bevel-properties-section.md) <br/> |
|BevelDepthColor  <br/> |Determines the color of the bevel's depth, as an RGB value or as determined by the active theme. |[BevelDepthColor Cell (Bevel Properties Section)](beveldepthcolor-cell-bevel-properties-section.md) <br/> |
|BevelDepthSize  <br/> |Determines the size of the bevel's depth in points. |[BevelDepthSize Cell (Bevel Properties Section)](beveldepthsize-cell-bevel-properties-section.md) <br/> |
|BevelLightingAngle  <br/> |Determines the angle of lightning in relation to the bevel in degrees. |[BevelLightingAngle Cell (Bevel Properties Section)](bevellightingangle-cell-bevel-properties-section.md) <br/> |
|BevelLightingType  <br/> |Determines the type of lighting used by the bevel effect. |[BevelLightingType Cell (Bevel Properties Section)](bevellightingtype-cell-bevel-properties-section.md) <br/> |
|BevelMaterialType  <br/> |Determines the type of material the bevel is composed of. |[BevelMaterialType Cell (Bevel Properties Section)](bevelmaterialtype-cell-bevel-properties-section.md) <br/> |
|BevelTopHeight  <br/> |Determines the height of a shape's top bevel in points. |[BevelTopHeight Cell (Bevel Properties Section)](beveltopheight-cell-bevel-properties-section.md) <br/> |
|BevelTopType  <br/> |Determines the type of bevel on a shape's top edge. |[BevelTopType Cell (Bevel Properties Section)](beveltoptype-cell-bevel-properties-section.md) <br/> |
|BevelTopWidth  <br/> |Determines the width of the top bevel in points. |[BevelTopWidth Cell (Bevel Properties Section)](beveltopwidth-cell-bevel-properties-section.md) <br/> |
|BlockSizeX  <br/> |Determines the horizontal block size, the area in which each of your shapes must fit on the drawing page when you lay out shapes by using the Configure Layout dialog box. |[BlockSizeX Cell (Page Layout Section)](blocksizex-cell-page-layout-section.md) <br/> |
|BlockSizeY  <br/> |Determines the vertical block size, the area in which each of your shapes must fit on the drawing page when you lay out shapes by using the Configure Layout dialog. |[BlockSizeY Cell (Page Layout Section)](blocksizey-cell-page-layout-section.md) <br/> |
|Blur  <br/> |Blurs or softens a bitmap image. The default value is 0%. |[Blur Cell (Image Properties Section)](blur-cell-image-properties-section.md) <br/> |
|BottomMargin  <br/> |Determines the distance between the bottom border of the text block and the last line of text it contains. |[BottomMargin Cell (Text Block Format Section)](bottommargin-cell-text-block-format-section.md) <br/> |
|Brightness  <br/> |Adjusts the brightness of a bitmap image. |[Brightness Cell (Image Properties Section](brightness-cell-image-properties-section.md) <br/> |
|Calendar  <br/> |Determines the calendar that is used when a cell formula contains Date information. |[Calendar Cell (Miscellaneous Section)](calendar-cell-miscellaneous-section.md) <br/> |
|Calendar  <br/> |Determines the calendar that is used for shape data when the data type is Date. |[Calendar Cell (Shape Data Section)](calendar-cell-shape-data-section.md) <br/> |
|Calendar  <br/> |Determines the calendar that is used for a text field when the data type is Date. |[Calendar Cell (Text Fields Section)](calendar-cell-text-fields-section.md) <br/> |
|CenterX  <br/> |Determines whether the drawing page is centered horizontally on the printer page. |[CenterX Cell (Print Properties Section)](centerx-cell-print-properties-section.md) <br/> |
|CenterY  <br/> |Determines whether the drawing page is centered vertically on the printer page. |[CenterY Cell (Print Properties Section)](centery-cell-print-properties-section.md) <br/> |
|ClippingPath  <br/> |Contains a reference to the geometry of the path that an image is bounded by. |[ClippingPath Cell (Foreign Image Info Section)](clippingpath-cell-foreign-image-info-section.md) <br/> |
|ColorSchemeIndex  <br/> |Determines the color scheme of a theme that is applied to the shape, as an integer. |[ColorSchemeIndex Cell (Theme Properties Section)](colorschemeindex-cell-theme-properties-section.md) <br/> |
|Comment  <br/> |Contains the text that appears in a comment. |[Comment Cell (Annotation Section)](comment-cell-annotation-section.md) <br/> |
|Comment  <br/> |Contains the comment text in string format for a shape. |[Comment Cell (Miscellaneous Section)](comment-cell-miscellaneous-section.md) <br/> |
|CompoundType  <br/> |Determines the compound type of the line of a shape. |[CompoundType Cell (Line Format Section)](compoundtype-cell-line-format-section.md) <br/> |
|ConFixedCode  <br/> |Determines when a connector reroutes. |[ConFixedCode Cell (Shape Layout Section)](confixedcode-cell-shape-layout-section.md) <br/> |
|ConLineJumpCode  <br/> |Determines when a connector jumps. |[ConLineJumpCode Cell (Shape Layout Section)](conlinejumpcode-cell-shape-layout-section.md) <br/> |
|ConLineJumpDirX  <br/> |Determines the line jump direction for line jumps occurring on a horizontal dynamic connector for a shape. |[ConLineJumpDirX Cell (Shape Layout Section)](conlinejumpdirx-cell-shape-layout-section.md) <br/> |
|ConLineJumpDirY  <br/> |Determines the line jump direction for line jumps occurring on a vertical dynamic connector for a shape. |[ConLineJumpDirY Cell (Shape Layout Section)](conlinejumpdiry-cell-shape-layout-section.md) <br/> |
|ConLineJumpStyle  <br/> |Determines the line jump style for line jumps on a dynamic connector. |[ConLineJumpStyle Cell (Shape Layout Section)](conlinejumpstyle-cell-shape-layout-section.md) <br/> |
|ConLineRouteExt  <br/> |Determines the appearance of a connector. |[ConLineRouteExt Cell (Shape Layout Section)](conlinerouteext-cell-shape-layout-section.md) <br/> |
|ConnectorSchemeIndex  <br/> |Determines the connector scheme of a theme that is applied to the shape, as an integer. |[ConnectorSchemeIndex Cell (Theme Properties Section)](connectorschemeindex-cell-theme-properties-section.md) <br/> |
|Contrast  <br/> |Adjusts the contrast of a bitmap image. |[Contrast Cell (Image Properties Section)](contrast-cell-image-properties-section.md) <br/> |
|Copyright  <br/> |Contains a string representing a human-readable copyright statement  <br/> ||
|CtrlAsInput  <br/> |Determines which shape is the parent when using shapes with control handles. This cell sets the behavior for all the shapes on the drawing page. |[CtrlAsInput Cell (Page Layout Section)](ctrlasinput-cell-page-layout-section.md) <br/> |
|DefaultTabStop  <br/> |Determines the interval of the default tab stops in a text block. |[DefaultTabstop Cell (Text Block Format Section)](defaulttabstop-cell-text-block-format-section.md) <br/> |
|Denoise  <br/> |Removes noise (pixels with randomly distributed color levels) from a bitmap image. |[Denoise Cell (Image Properties Section)](denoise-cell-image-properties-section.md) <br/> |
|DisplayLevel  <br/> |Determines the display level band (the relative range of Z-order grouping) for the shape. |[DisplayLevel Cell (Shape Layout Section)](displaylevel-cell-shape-layout-section.md) <br/> |
|DisplayMode  <br/> |Determines how the group shape and its members are displayed. |[DisplayMode Cell (Group Properties Section)](displaymode-cell-group-properties-section.md) <br/> |
|DisplayMode  <br/> |Determines whether the action tag appears when the user moves the pointer over the tag, when the shape is selected, or all the time. |[DisplayMode Cell (Smart Tags Section)](displaymode-cell-action-tags-section.md) <br/> |
|DistanceFromGround  <br/> |Determines the distance the object is raised from the ground in points when rotated in 3-D. |[DistanceFromGround Cell (3-D Rotation Properties)](distancefromground-cell-3-d-rotation-properties.md) <br/> |
|DocLangID  <br/> |Indicates the default language for the document. |[DocLangID Cell (Document Properties Section)](doclangid-cell-document-properties-section.md) <br/> |
|DocLockDuplicatePage  <br/> |Determines whether pages in the document can be duplicated, as a Boolean. |[DocLockDuplicatePage Cell (Document Properties Section)](doclockduplicatepage-cell-document-properties-section.md) <br/> |
|DocLockReplace  <br/> |Determines whether the replace shape UI should be disabled for this document. |[DocLockReplace Cell (Document Properties Section)](doclockreplace-cell-document-properties-section.md) <br/> |
|DontMoveChildren  <br/> |Determines whether you can drag shapes in a group using the mouse. |[DontMoveChildren Cell (Group Properties Section)](dontmovechildren-cell-group-properties-section.md) <br/> |
|DrawingResizeType  <br/> |Determines whether the drawing page resizes automatically to fit the diagram. |[DrawingResizeType Cell (Page Properties Section)](drawingresizetype-cell-page-properties-section.md) <br/> |
|DrawingScale  <br/> |Represents the value of the drawing unit in the current drawing scale. |[DrawingScale Cell (Page Properties Section)](drawingscale-cell-page-properties-section.md) <br/> |
|DrawingScaleType  <br/> |Determines the drawing scale selected in the Page Setup dialog box (click the Page Setup arrow on the Home tab). |[DrawingScaleType Cell (Page Properties Section)](drawingscaletype-cell-page-properties-section.md) <br/> |
|DrawingSizeType  <br/> |Determines the drawing size. |[DrawingSizeType Cell (Page Properties Section)](drawingsizetype-cell-page-properties-section.md) <br/> |
|DropOnPageScale  <br/> |Contains the percentage by which a shape is scaled when dropped on the drawing page. |[DropOnPageScale Cell (Miscellaneous Section)](droponpagescale-cell-miscellaneous-section.md) <br/> |
|DynamicsOff  <br/> |Determines whether placeable shapes move and connectors reroute around other shapes and connectors on the drawing page. |[DynamicsOff Cell (Page Layout Section)](dynamicsoff-cell-page-layout-section.md) <br/> |
|DynFeedback  <br/> |Changes the type of visual feedback provided to users when they drag a connector. |[DynFeedback Cell (Miscellaneous Section)](dynfeedback-cell-miscellaneous-section.md) <br/> |
|EffectSchemeIndex  <br/> |Determines the effect scheme of the theme applied to a shape, as an integer. |[EffectSchemeIndex Cell (Theme Properties Section)](effectschemeindex-cell-theme-properties-section.md) <br/> |
|EmbellishmentIndex  <br/> |Changes the look and feel (embellishment) of callouts, containers, timelines, and organization chart shapes. |[EmbellishmentIndex Cell (Theme Properties Section)](embellishmentindex-cell-theme-properties-section.md) <br/> |
|EnableFillProps  <br/> |Determines whether a style includes fill properties. |[EnableFillProps Cell (Style Properties Section)](enablefillprops-cell-style-properties-section.md) <br/> |
|EnableGrid  <br/> |Determines whether the application lays out shapes based on an internal, invisible page grid when you configure the layout in the Configure Layout dialog box. |[EnableGrid Cell (Page Layout Section)](enablegrid-cell-page-layout-section.md) <br/> |
|EnableLineProps  <br/> |Determines whether a style includes line properties. |[EnableLineProps Cell (Style Properties Section)](enablelineprops-cell-style-properties-section.md) <br/> |
|EnableTextProps  <br/> |Determines whether a style includes text properties. |[EnableTextProps Cell (Style Properties Section)](enabletextprops-cell-style-properties-section.md) <br/> |
|EndArrow  <br/> |Indicates whether a line has an arrowhead or other line end format at its last vertex. |[EndArrow Cell (Line Format Section)](endarrow-cell-line-format-section.md) <br/> |
|EndArrowSize  <br/> |Determines the size of the arrowhead at the end of the line. |[EndArrowSize Cell (Line Format Section)](endarrowsize-cell-line-format-section.md) <br/> |
|EndTrigger  <br/> |Contains a trigger formula generated by the application that determines whether to move the endpoint of a 1-D shape to maintain its connection to another shape. |[EndTrigger Cell (Glue Info Section)](endtrigger-cell-glue-info-section.md) <br/> |
|EndX  <br/> |Represents the x-coordinate of the endpoint of the 1-D shape, in relation to the origin of its parent. |[EndX Cell (1-D Endpoints Section)](endx-cell-1-d-endpoints-section.md) <br/> |
|EndY  <br/> |Represents the y-coordinate of the endpoint of the 1-D shape, in relation to the origin of its parent. |[EndY Cell (1-D Endpoints Section)](endy-cell-1-d-endpoints-section.md) <br/> |
|EventDblClick  <br/> |An event cell that is evaluated when a shape is double-clicked. |[EventDblClick Cell (Events Section)](eventdblclick-cell-events-section.md) <br/> |
|EventDrop  <br/> |An event cell that is evaluated when a shape is dropped on the drawing page, either as an instance or when the shape is duplicated or pasted. |[EventDrop Cell (Events Section)](eventdrop-cell-events-section.md) <br/> |
|EventMultiDrop  <br/> |An event cell that is evaluated when multiple shapes are dropped on the drawing page, either as instances or when shapes are duplicated or pasted. |[EventMultiDrop Cell (Events Section)](eventmultidrop-cell-events-section.md) <br/> |
|EventXFMod  <br/> |An event cell that is evaluated when a shape's position or orientation on the page is transformed ("XF"). |[EventXFMod Cell (Events Section)](eventxfmod-cell-events-section.md) <br/> |
|FillBkgnd  <br/> |Determines the color used for the background (fill) of the shape's fill pattern. |[FillBkgnd Cell (Fill Format Section)](fillbkgnd-cell-fill-format-section.md) <br/> |
|FillBkgndTrans  <br/> |Determines the transparency level for the background (fill) color of the shape's fill pattern. |[FillBkgndTrans Cell (Fill Format Section)](fillbkgndtrans-cell-fill-format-section.md) <br/> |
|FillForegnd  <br/> |Determines the color used for the foreground (stroke) of the shape's fill pattern. |[FillForegnd Cell (Fill Format Section)](fillforegnd-cell-fill-format-section.md) <br/> |
|FillForegndTrans  <br/> |Determines the transparency level for the background (fill) color of the shape's fill pattern. |[FillForegndTrans Cell (Fill Format Section)](fillforegndtrans-cell-fill-format-section.md) <br/> |
|FillGradientAngle  <br/> |Determines the angle of the fill gradient for gradients with a linear direction, in degrees. |[FillGradientAngle Cell (Gradient Properties Section)](fillgradientangle-cell-gradient-properties-section.md) <br/> |
|FillGradientDir  <br/> |Determines the direction of the fill gradient. A gradient can be linear, radial, rectangular, or follow a path. |[FillGradientDir Cell (Gradient Properties Section)](fillgradientdir-cell-gradient-properties-section.md) <br/> |
|FillGradientEnabled  <br/> |Determines whether a fill gradient is enabled for this shape. |[FillGradientEnabled Cell (Gradient Properties Section)](fillgradientenabled-cell-gradient-properties-section.md) <br/> |
|FillPattern  <br/> |Determines the fill pattern for the shape. To specify a custom fill pattern, use the USE function in this cell. |[FillPattern Cell (Fill Format Section)](fillpattern-cell-fill-format-section.md) <br/> |
|FlipX  <br/> |Indicates whether the shape has been flipped horizontally. |[FlipX Cell (Shape Transform Section)](flipx-cell-shape-transform-section.md) <br/> |
|FlipY  <br/> |Indicates whether the shape has been flipped vertically. |[FlipY Cell (Shape Transform Section)](flipy-cell-shape-transform-section.md) <br/> |
|FontSchemeIndex  <br/> |Determines the font scheme of a theme that is applied to the shape, as an integer. |[FontSchemeIndex Cell (Theme Properties Section](fontschemeindex-cell-theme-properties-section.md) <br/> |
|Gamma  <br/> |Adjusts or corrects the intensity of an image for a particular output device, such as a monitor or scanner. The default value is 1 (no correction). |[Gamma Cell (Image Properties Section)](gamma-cell-image-properties-section.md) <br/> |
|GlowColor  <br/> |Determines the color used for the stroke of the external glow applied to a shape, as an RGB or theme value. |[GlowColor Cell (Additional Effect Properties Section)](glowcolor-cell-additional-effect-properties-section.md) <br/> |
|GlowColorTrans  <br/> |Determines the transparency level for the color used for the stroke of the shape's glow, as a percentage. |[GlowColorTrans Cell (Additional Effect Properties Section)](glowcolortrans-cell-additional-effect-properties-section.md) <br/> |
|GlowSize  <br/> |Determines the size of the external glow of a shape in points. |[GlowSize Cell (Additional Effect Properties Section)](glowsize-cell-additional-effect-properties-section.md) <br/> |
|GlueType  <br/> |Determines whether a 1-D shape uses static (point-to-point) or dynamic (shape-to-shape) glue when it is glued to another shape. |[GlueType Cell (Glue Info Section)](gluetype-cell-glue-info-section.md) <br/> |
|Height  <br/> |Determines the height of the shape in drawing units. |[Height Cell (Shape Transform Section)](height-cell-shape-transform-section.md) <br/> |
|HelpTopic  <br/> |Specifies the help topic ID of the shape. ||
|HideForApply  <br/> |Determines where a style is shown in the Microsoft Visio user interface. |[HideForApply Cell (Style Properties Section)](hideforapply-cell-style-properties-section.md) <br/> |
|HideText  <br/> |Hides the text for a shape. |[HideText Cell (Miscellaneous Section)](hidetext-cell-miscellaneous-section.md) <br/> |
|ImgHeight  <br/> |Determines the height of the object's image within its border. |[ImgHeight Cell (Foreign Image Info Section)](imgheight-cell-foreign-image-info-section.md) <br/> |
|ImgOffsetX  <br/> |Determines the distance the object is offset horizontally from the origin of the object's border. |[ImgOffsetX Cell (Foreign Image Info Section)](imgoffsetx-cell-foreign-image-info-section.md) <br/> |
|ImgOffsetY  <br/> |Determines the distance the object is offset vertically from the origin of the object's border. |[ImgOffsetY Cell (Foreign Image Info Section)](imgoffsety-cell-foreign-image-info-section.md) <br/> |
|ImgWidth  <br/> |Determines the width of the object's image within its border. |[ImgWidth Cell (Foreign Image Info Section)](imgwidth-cell-foreign-image-info-section.md) <br/> |
|InhibitSnap  <br/> |Determines whether the shapes on a foreground page snap to other objects on the page and shapes on the background page. |[InhibitSnap Cell (Page Properties Section)](inhibitsnap-cell-page-properties-section.md) <br/> |
|IsDropSource  <br/> |Determines whether the shape can be added to a group by dropping it onto the group. |[IsDropSource Cell (Miscellaneous Section)](isdropsource-cell-miscellaneous-section.md) <br/> |
|IsDropTarget  <br/> |Determines whether the group allows you to add a shape to it by dropping it on the group. |[IsDropTarget Cell (Group Properties Section)](isdroptarget-cell-group-properties-section.md) <br/> |
|IsSnapTarget  <br/> |Determines whether you snap to a group or to shapes within the group. |[IsSnapTarget Cell (Group Properties Section)](issnaptarget-cell-group-properties-section.md) <br/> |
|IsTextEditTarget  <br/> |Determines text assignment for a group. |[IsTextEditTarget Cell (Group Properties Section)](istextedittarget-cell-group-properties-section.md) <br/> |
|KeepTextFlat  <br/> |Indicates whether a shape's text will ignore the shape's rotation in 3-D. Does not apply to 2-D rotation. |[KeepTextFlat Cell (3-D Rotation Properties Section)](keeptextflat-cell-3-d-rotation-properties-section.md) <br/> |
|LangID  <br/> |Indicates the language in which the comment was entered. |[LangID Cell (Annotation Section)](langid-cell-annotation-section.md) <br/> |
|LangID  <br/> |Indicates the language in which the text was entered. |[LangID Cell (Character Section)](langid-cell-character-section.md) <br/> |
|LangID  <br/> |Indicates the language in which cell formulas were created. |[LangID Cell (Miscellaneous Section)](langid-cell-miscellaneous-section.md) <br/> |
|LangID  <br/> |Indicates the language in which the shape data value was entered. |[LangID Cell (Shape Data Section)](langid-cell-shape-data-section.md) <br/> |
|LayerMember  <br/> |Specifies layer membership of the shape based on the zero-based index of layers for the page. If a shape is assigned to more than one layer, each layer index appears separated by a semicolon. ||
|LeftMargin  <br/> |Determines the distance between the left border of the text block and the text it contains. |[LeftMargin Cell (Text Block Format Section)](leftmargin-cell-text-block-format-section.md) <br/> |
|LineAdjustFrom  <br/> |Determines which dynamic connectors the application spaces apart if they route on top of each other. |[LineAdjustFrom Cell (Page Layout Section)](lineadjustfrom-cell-page-layout-section.md) <br/> |
|LineAdjustTo  <br/> |Determines which dynamic connectors line up on top of one another. |[LineAdjustTo Cell (Page Layout Section)](lineadjustto-cell-page-layout-section.md) <br/> |
|LineCap  <br/> |Indicates whether a line has rounded, square, or extended line caps. |[LineCap Cell (Line Format Section)](linecap-cell-line-format-section.md) <br/> |
|LineColor  <br/> |Determines the line color of the shape. |[LineColor Cell (Line Format Section)](linecolor-cell-line-format-section.md) <br/> |
|LineColorTrans  <br/> |Determines the transparency level of a shape's line color. |[LineColorTrans Cell (Line Format Section)](linecolortrans-cell-line-format-section.md) <br/> |
|LineGradientAngle  <br/> |Determines the angle of the line gradient for a linear gradient, from 0 to 359.9 degrees. |[LineGradientAngle Cell (Gradient Properties Section)](linegradientangle-cell-gradient-properties-section.md) <br/> |
|LineGradientDir  <br/> |Determines the direction of the line gradient. A gradient can be linear, radial, rectangular, or follow a path. |[LineGradientDir Cell (Gradient Properties Section)](linegradientdir-cell-gradient-properties-section.md) <br/> |
|LineGradientEnabled  <br/> |Determines whether a line gradient is enabled for a line or border of a shape. |[LineGradientEnabled Cell (Gradient Properties Section)](linegradientenabled-cell-gradient-properties-section.md) <br/> |
|LineJumpCode  <br/> |Determines the connectors to which you want to add jumps. ||
|LineJumpFactorX  <br/> |Determines the size of line jumps on horizontal dynamic connectors on the page, relative to the value of the LineToLineX cell. The value of this cell can range from 0 to 10 but fractional values from 0 to 1 are suggested. |[LineJumpFactorX Cell (Page Layout Section)](linejumpfactorx-cell-page-layout-section.md) <br/> |
|LineJumpFactorY  <br/> |Determines the size of line jumps on vertical dynamic connectors on the page, relative to the value of the LineToLineY cell. The value of this cell can range from 0 to 10 but fractional values from 0 to 1 are suggested. |[LineJumpFactorY Cell (Page Layout Section)](linejumpfactory-cell-page-layout-section.md) <br/> |
|LineJumpStyle  <br/> |Determines the line jump style for all connectors on the drawing page that don't have a local line jump style. |[LineJumpStyle Cell (Page Layout Section)](linejumpstyle-cell-page-layout-section.md) <br/> |
|LinePattern  <br/> |Determines the line pattern of the shape. The value entered in the LinePattern cell is a number that is an index into a collection of line patterns. |[LinePattern Cell (Line Format Section)](linepattern-cell-line-format-section.md) <br/> |
|LineRouteExt  <br/> |Determines the default appearance for all connectors on a drawing page. |[LineRouteExt Cell (Page Layout Section)](linerouteext-cell-page-layout-section.md) <br/> |
|LineToLineX  <br/> |Determines the horizontal clearance between all connectors on the drawing page. |[LineToLineX Cell (Page Layout Section)](linetolinex-cell-page-layout-section.md) <br/> |
|LineToLineY  <br/> |Determines the vertical clearance between all connectors on the drawing page. |[LineToLineY Cell (Page Layout Section)](linetoliney-cell-page-layout-section.md) <br/> |
|LineToNodeX  <br/> |Determines the horizontal clearance between all connectors and shapes on the drawing page. |[LineToNodeX Cell (Page Layout Section)](linetonodex-cell-page-layout-section.md) <br/> |
|LineToNodeY  <br/> |Determines the vertical clearance between all connectors and shapes on the drawing page. |[LineToNodeY Cell (Page Layout Section)](linetonodey-cell-page-layout-section.md) <br/> |
|LineWeight  <br/> |Determines the line weight of a shape. Set the line weight by entering a number with a valid unit of measure. |[LineWeight Cell (Line Format Section)](lineweight-cell-line-format-section.md) <br/> |
|LocalizeMerge  <br/> |Determines whether shapes are localized when copied between documents. |[LocalizeMerge Cell (Miscellaneous Section)](localizemerge-cell-miscellaneous-section.md) <br/> |
|LockAspect  <br/> |Locks the aspect ratio of the shape so that the shape can only be sized proportionally; it cannot be sized in a single dimension. |[LockAspect Cell (Protection Section)](lockaspect-cell-protection-section.md) <br/> |
|LockBegin  <br/> |Locks the begin point (BeginX, BeginY) of a 1-D shape to a specific location. |[LockBegin Cell (Protection Section)](lockbegin-cell-protection-section.md) <br/> |
|LockCalcWH  <br/> |Locks a shape's selection rectangle so it cannot be recalculated when a vertex is edited or a row type is changed in the Geometry section. |[LockCalcWH Cell (Protection Section)](lockcalcwh-cell-protection-section.md) <br/> |
|LockCrop  <br/> |Locks an object from another program against being cropped with the Crop tool. |[LockCrop Cell (Protection Section)](lockcrop-cell-protection-section.md) <br/> |
|LockCustProp  <br/> |Determines whether the user can add, delete, or modify shape data in the user interface (UI) by using the Define Shape Data dialog box or the shortcut menu for the Shape Data window. |[LockCustProp Cell (Protection Section)](lockcustprop-cell-protection-section.md) <br/> |
|LockDelete  <br/> |Locks the shape so that it cannot be deleted. |[LockDelete Cell (Protection Section)](lockdelete-cell-protection-section.md) <br/> |
|LockEnd  <br/> |Locks the endpoint (EndX, EndY) of a 1-D shape to a specific location. |[LockEnd Cell (Protection Section)](lockend-cell-protection-section.md) <br/> |
|LockFormat  <br/> |Locks the formatting of a shape so it cannot be changed. |[LockFormat Cell (Protection Section)](lockformat-cell-protection-section.md) <br/> |
|LockFromGroupFormat  <br/> |Blocks format changes to a group shape from being propagated to its sub-shapes, while still allowing users to format selected sub-shapes directly. The value of the LockFromGroupFormat cell corresponds to the From group formatting check box setting in the Protection dialog box. |[LockFromGroupFormat Cell (Protection Section)](lockfromgroupformat-cell-protection-section.md) <br/> |
|LockGroup  <br/> |Locks a group so that it cannot be ungrouped. |[LockGroup Cell (Protection Section)](lockgroup-cell-protection-section.md) <br/> |
|LockHeight  <br/> |Locks the height of the shape so that its height remains unchanged when the shape is resized. |[LockHeight Cell (Protection Section)](lockheight-cell-protection-section.md) <br/> |
|LockMoveX  <br/> |Locks the horizontal position of the shape so it cannot be moved horizontally. |[LockMoveX Cell (Protection Section)](lockmovex-cell-protection-section.md) <br/> |
|LockMoveY  <br/> |Locks the vertical position of the shape so it cannot be moved vertically. |[LockMoveY Cell (Protection Section)](lockmovey-cell-protection-section.md) <br/> |
|LockPreview  <br/> |Determines whether a preview is saved each time you save a drawing. |[LockPreview Cell (Document Properties Section)](lockpreview-cell-document-properties-section.md) <br/> |
|LockReplace  <br/> |Indicates whether a shape can participate in a replacement operation (as either a target or a replacement shape). |[LockReplace Cell (Protection Section)](lockreplace-cell-protection-section.md) <br/> |
|LockRotate  <br/> |Locks 2-D shapes against being rotated with the rotation handle or the Rotate Left 90° or Rotate Right 90° command. |[LockRotate Cell (Protection Section)](lockrotate-cell-protection-section.md) <br/> |
|LockSelect  <br/> |Prevents a shape from being selected. |[LockSelect Cell (Protection Section)](lockselect-cell-protection-section.md) <br/> |
|LockTextEdit  <br/> |Locks the text of a shape so that it cannot be edited. |[LockTextEdit Cell (Protection Section)](locktextedit-cell-protection-section.md) <br/> |
|LockThemeColors  <br/> |Prevents application of theme colors to the shape. The value of the LockThemeColors cell corresponds to the From theme colors check box setting in the Protection dialog box. |[LockThemeColors Cell (Protection Section)](lockthemecolors-cell-protection-section.md) <br/> |
|LockThemeConnectors  <br/> |Prevents the ConnectorsSchemeIndex cell in the Theme Properties row from being altered by applying a new theme or selecting a new connector scheme. Does not prevent users from manually editing this value in the ShapeSheet. |[LockThemeConnectors Cell (Protection Section)](lockthemeconnectors-cell-protection-section.md) <br/> |
|LockThemeEffects  <br/> |Corresponds to the From theme effects check box setting in the Protection dialog box. |[LockThemeEffects Cell (Protection Section)](lockthemeeffects-cell-protection-section.md) <br/> |
|LockThemeFonts  <br/> |Prevents the FontIndex cell in the Theme Properties row from being altered by applying a new theme. Does not prevent users from manually editing this value in the ShapeSheet. |[LockThemeFonts Cell (Protection Section)](lockthemefonts-cell-protection-section.md) <br/> |
|LockThemeIndex  <br/> |Prevents ThemeIndex cell in Theme Properties row from being altered by applying a new theme or selecting a new connector scheme. Does not prevent users from manually editing this value in the ShapeSheet. |[LockThemeIndex Cell (Protection Section)](lockthemeindex-cell-protection-section.md) <br/> |
|LockVariation  <br/> |Determines whether the theme variation applied to the page or shape can be changed, as a Boolean. |[LockVariation Cell (Protection Section)](lockvariation-cell-protection-section.md) <br/> |
|LockVtxEdit  <br/> |Locks the vertices of a shape so that they cannot be edited. |[LockVtxEdit Cell (Protection Section)](lockvtxedit-cell-protection-section.md) <br/> |
|LockWidth  <br/> |Locks the width of the shape so that its width remains unchanged when the shape is sized. |[LockWidth Cell (Protection Section)](lockwidth-cell-protection-section.md) <br/> |
|LocPinX  <br/> |Represents the x-coordinate of the shape's pin (center of rotation) in relation to the origin of the shape. The default formula for determining LocPinX is: = Width \* 0.5. |[LocPinX Cell (Shape Transform Section)](locpinx-cell-shape-transform-section.md) <br/> |
|LockPinY  <br/> |Represents the y-coordinate of the shape's pin (center of rotation) in relation to the origin of the shape. The default formula for determining LocPinY is: = Height \* 0.5. |[LocPinY Cell (Shape Transform Section)](locpiny-cell-shape-transform-section.md) <br/> |
|NoAlignBox  <br/> |Switches the display of the selection rectangle on and off for the selected shape. |[NoAlignBox Cell (Miscellaneous Section)](noalignbox-cell-miscellaneous-section.md) <br/> |
|NoCoauth  <br/> |Sets whether a document stored on a SharePoint 2013 server or on Microsoft OneDrive can be edited by multiple authors simultaneously in a coauthoring session. |[NoCoauth Cell (Document Properties Section)](nocoauth-cell-document-properties-section.md) <br/> |
|NoCtlHandles  <br/> |Prevents control handles from appearing when the shape is selected. |[NoCtlHandles Cell (Miscellaneous Section)](noctlhandles-cell-miscellaneous-section.md) <br/> |
|NoLiveDynamics  <br/> |Determines whether a shape dynamically resizes or rotates as you are manipulating it. |[NoLiveDynamics Cell (Miscellaneous Section)](nolivedynamics-cell-miscellaneous-section.md) <br/> |
|NonPrinting  <br/> |Switches printing on and off for the selected shape. |[NonPrinting Cell (Miscellaneous Section)](nonprinting-cell-miscellaneous-section.md) <br/> |
|NoObjHandles  <br/> |Switches the display of selection handles on and off for the selected shape. |[NoObjHandles Cell (Miscellaneous Section)](noobjhandles-cell-miscellaneous-section.md) <br/> |
|NoProofing  <br/> |Determine whether spelling will be automatically corrected and whether spelling errors will be displayed for the selected shape. ||
|ObjType  <br/> |Determines whether objects are placeable or routable in diagrams when you use the Configure Layout dialog box to lay out shapes. |[ObjType Cell (Miscellaneous Section)](objtype-cell-miscellaneous-section.md) <br/> |
|OnPage  <br/> |Indicates whether the drawing is printed on a specific number of printer pages. |[OnPage Cell (Print Properties Section)](onpage-cell-print-properties-section.md) <br/> |
|OutputFormat  <br/> |Determines the output format for a drawing. Drawing pages are usually formatted for printing (default); however, you can choose other output formats. |[OutputFormat Cell (Document Properties Section)](outputformat-cell-document-properties-section.md) <br/> |
|PageBottomMargin  <br/> |Specifies the margin at the bottom of the printed page. |[PageBottomMargin Cell (Print Properties Section)](pagebottommargin-cell-print-properties-section.md) <br/> |
|PageHeight  <br/> |Contains the height of the printed page in drawing units. |[PageHeight Cell (Page Properties Section)](pageheight-cell-page-properties-section.md) <br/> |
|PageLeftMargin  <br/> |Specifies the margin on the left of the printed page. |[PageLeftMargin Cell (Print Properties Section)](pageleftmargin-cell-print-properties-section.md) <br/> |
|PageLineJumpDirX  <br/> |Determines the direction of line jumps on horizontal dynamic connectors on the drawing page for which you haven't applied a local jump direction. |[PageLineJumpDirX Cell (Page Layout Section)](pagelinejumpdirx-cell-page-layout-section.md) <br/> |
|PageLineJumpDirY  <br/> |Determines the direction of line jumps on vertical dynamic connectors on the drawing page for which you haven't applied a local jump direction. |[PageLineJumpDirY Cell (Page Layout Section)](pagelinejumpdiry-cell-page-layout-section.md) <br/> |
|PageLockDuplicate  <br/> |Determines whether the page can be duplicated, as a Boolean. |[PageLockDuplicate Cell (Page Properties Section)](pagelockduplicate-cell-page-properties-section.md) <br/> |
|PageLockReplace  <br/> |Indicates whether the Replace Shape button should be disabled for this page. |[PageLockReplace Cell (Page Properties Section)](pagelockreplace-cell-page-properties-section.md) <br/> |
|PageRightMargin  <br/> |Specifies the margin on the right of the printed page. |[PageRightMargin Cell (Print Properties Section)](pagerightmargin-cell-print-properties-section.md) <br/> |
|PageScale  <br/> |Determines the value of the page unit in the current drawing scale. The drawing scale for the page is the ratio of the page unit shown in the PageScale cell to the drawing unit shown in the DrawingScale cell. |[PageScale Cell (Page Properties Section)](pagescale-cell-page-properties-section.md) <br/> |
|PageShapeSplit  <br/> |Indicates whether shapes on the page can be automatically split. |[PageShapeSplit Cell (Page Layout Section)](pageshapesplit-cell-page-layout-section.md) <br/> |
|PagesX  <br/> |Determines the number of printer pages on which to fit the drawing page horizontally. |[PagesX Cell (Print Properties Section)](pagesx-cell-print-properties-section.md) <br/> |
|PagesY  <br/> |Determines the number of printer pages on which to fit the drawing page vertically. |[PagesY Cell (Print Properties Section)](pagesy-cell-print-properties-section.md) <br/> |
|PageTopMargin  <br/> |Specifies the margin at the top of the printer page. |[PageTopMargin Cell (Print Properties Section)](pagetopmargin-cell-print-properties-section.md) <br/> |
|PageWidth  <br/> |Determines the width of the printed page in drawing units. |[PageWidth Cell (Page Properties Section)](pagewidth-cell-page-properties-section.md) <br/> |
|PaperKind  <br/> |Specifies the type of paper on which to print the page. |[PaperKind Cell (Print Properties Section)](paperkind-cell-print-properties-section.md) <br/> |
|PaperSource  <br/> |Determines the paper source for the page. |[PaperSource Cell (PrintProperties Section)](papersource-cell-printproperties-section.md) <br/> |
|Perspective  <br/> |Determines the perspective angle for a perspective rotation, in degrees (0 to 359.9). |[Perspective Cell (3-D Rotation Properties Section)](perspective-cell-3-d-rotation-properties-section.md) <br/> |
|PinX  <br/> |Represents the x-coordinate of the shape's pin (center of rotation) in relation to the origin of its parent. |[PinX Cell (Shape Transform Section)](pinx-cell-shape-transform-section.md) <br/> |
|PinY  <br/> |Represents the y-coordinate of the shape's pin (center of rotation) in relation to the origin of its parent. |[PinY Cell (Shape Transform Section)](piny-cell-shape-transform-section.md) <br/> |
|PlaceDepth  <br/> |Determines the method by which the drawing is analyzed before creating the layout, and determines the type of layout. |[PlaceDepth Cell (Page Layout Section)](placedepth-cell-page-layout-section.md) <br/> |
|PlaceFlip  <br/> |Determines how placeable shapes flip and/or rotate on a page when you use the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). |[PlaceFlip Cell (Page Layout Section)](placeflip-cell-page-layout-section.md) <br/> |
|PlaceStyle  <br/> |Determines how shapes are placed on the page when you are laying out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). |[PlaceStyle Cell (Page Layout Section)](placestyle-cell-page-layout-section.md) <br/> |
|PlowCode  <br/> |Determines whether placeable shapes move away when you drop a placeable shape near another placeable shape on the drawing page. |[PlowCode Cell (Page Layout Section)](plowcode-cell-page-layout-section.md) <br/> |
|PreviewQuality  <br/> |Determines whether the drawing preview is draft quality or detailed. |[PreviewQuality Cell (Document Properties Section)](previewquality-cell-document-properties-section.md) <br/> |
|PreviewScope  <br/> |Determines whether your drawing includes a preview. If your drawing does include a preview, it determines whether the preview shows the first page only or all of the pages in the drawing. |[PreviewScope Cell (Document Properties Section)](previewscope-cell-document-properties-section.md) <br/> |
|PrintGrid  <br/> |Specifies whether to print the grid when printing a document page. |[PrintGrid Cell (Print Properties Section)](printgrid-cell-print-properties-section.md) <br/> |
|PrintPageOrientation  <br/> |Determines whether the page prints using portrait or landscape orientation. |[PrintPageOrientation Cell (Print Properties Section)](printpageorientation-cell-print-properties-section.md) <br/> |
|QuickStyleEffectsMatrix  <br/> |Determines the Quick Style effects that the shape inherits from the active theme, as an integer from 0-6. ||
|QuickStyleFillColor  <br/> |Determines which theme color that a shape's fill uses, as an integer from 0 to 7. |[QuickStyleFillColor Cell (Quick Style Section)](quickstylefillcolor-cell-quick-style-section.md) <br/> |
|QuickStyleFillMatrix  <br/> |Determines the Quick Style fill style that the shape inherits from the active theme, as an integer from 0-6. |[QuickStyleFillMatrix Cell (Quick Style Section)](quickstylefillmatrix-cell-quick-style-section.md) <br/> |
|QuickStyleFontColor  <br/> |Determines the font color from the Quick Styles that a shape's text inherits from the active theme, as an integer from 0-1. |[QuickStyleFontColor Cell (Quick Style Section)](quickstylefontcolor-cell-quick-style-section.md) <br/> |
|QuickStyleFontMatrix  <br/> |Determines the style of the font for each Quick Style, as an integer from 1 to 6. |[QuickStyleFontMatrix Cell (Quick Style Section)](quickstylefontmatrix-cell-quick-style-section.md) <br/> |
|QuickStyleLineColor  <br/> |Determines which theme color that a shape's line uses, as an integer from 0 to 7. |[QuickStyleLineColor Cell (Quick Style Section)](quickstylelinecolor-cell-quick-style-section.md) <br/> |
|QuickStyleLineMatrix  <br/> |Determines the Quick Style line style that the shape inherits, as an integer from 0-6. |[QuickStyleLineMatrix Cell (Quick Style Section)](quickstylelinematrix-cell-quick-style-section.md) <br/> |
|QuickStyleShadowColor  <br/> |Determines which theme color that a shape's shadow uses, as an integer from 0 to 7. |[QuickStyleShadowColor Cell (Quick Style Section)](quickstyleshadowcolor-cell-quick-style-section.md) <br/> |
|QuickStyleType  <br/> |Determines the type of Quick Style (2-dimensional, 1-dimensional, or connector) that the shape inherits. |[QuickStyleType Cell (Quick Style Section)](quickstyletype-cell-quick-style-section.md) <br/> |
|QuickStyleVariation  <br/> |Ensures text, line, and/or fill color visibility on a shape against a themed diagram background. ||
|ReflectionBlur  <br/> |Determines the amount of blur for a reflection on a shape, in points between 0.0 and 100.0. |[ReflectionBlur Cell (Additional Effect Properties Section)](reflectionblur-cell-additional-effect-properties-section.md) <br/> |
|ReflectionDist  <br/> |Determines the distance that a reflection is offset from a shape, in points from 0.0 to 100.0. |[ReflectionDist Cell (Additional Effect Properties Section)](reflectiondist-cell-additional-effect-properties-section.md) <br/> |
|ReflectionSize  <br/> |Determines the size of the reflection relative to the shape, as a percentage from 0.0 to 100.0%. A shape with a value of 0% in the ReflectionSize cell does not have a reflection; a value of 100% displays a complete mirror image of the shape. |[ReflectionSize Cell (Additional Effect Properties Section)](reflectionsize-cell-additional-effect-properties-section.md) <br/> |
|ReflectionTrans  <br/> |Determines the transparency of the reflection, as a percentage from 0 to 100%. |[ReflectionTrans Cell (Additional Effect Properties Section)](reflectiontrans-cell-additional-effect-properties-section.md) <br/> |
|Relationships  <br/> |Stores the relationships between containers, lists, callouts, and shapes. |[Relationships Cell (Shape Layout Section)](relationships-cell-shape-layout-section.md) <br/> |
|ReplaceCopyCells  <br/> |Indicates a list of cells in the ShapeSheet that are copied from an old shape to the replacement shape during a shape replacement operation. |[ReplaceCopyCells Cell (Change Shape Behavior Section)](replacecopycells-cell-change-shape-behavior-section.md) <br/> |
|ReplaceLockFormat  <br/> |Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. If the ReplaceLockFormat cell of a master shape is set to TRUE (1), the formatting values of the master overwrite all corresponding values of a shape being replaced by the master. |[ReplaceLockFormat Cell (Change Shape Behavior Section)](replacelockformat-cell-change-shape-behavior-section.md) <br/> |
|ReplaceLockShapeData  <br/> |Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. The ReplaceLockShapeData determines whether the shape data of the master shape overwrites all of the shape data of the shape being replaced. |[ReplaceLockShapeData Cell (Change Shape Behavior Section)](replacelockshapedata-cell-change-shape-behavior-section.md) <br/> |
|ReplaceLockText  <br/> |Indicates whether the values of specified cells in a master shape overwrite the values (including local values) of a shape being replaced during a shape replacement operation. The ReplaceLockText determines whether the text displayed on the Master overwrites the text of the shape being replaced. |[ReplaceLockText Cell (Change Shape Behavior Section)](replacelocktext-cell-change-shape-behavior-section.md) <br/> |
|ResizeMode  <br/> |Shows the current resize behavior setting for the shape. |[ResizeMode Cell (Shape Transform Section)](resizemode-cell-shape-transform-section.md) <br/> |
|ResizePage  <br/> |Determines whether to enlarge the page to enclose the drawing after laying out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). |[ResizePage Cell (Page Layout Section)](resizepage-cell-page-layout-section.md) <br/> |
|RightMargin  <br/> |Determines the distance between the right border of the text block and the text it contains. The default is 0.1 inch. |[RightMargin Cell (Text Block Format Section)](rightmargin-cell-text-block-format-section.md) <br/> |
|RotateGradientWithShape  <br/> |Determines whether a fill gradient rotates with a shape in 2D rotation, as a boolean. |[RotateGradientWithShape Cell (Gradient Properties Section)](rotategradientwithshape-cell-gradient-properties-section.md) <br/> |
|RotationType  <br/> |Determines whether the shape follows a parallel rotation, a perspective rotation, or an oblique rotation, as an integer from 0 to 6. |[RotationType Cell (3-D Rotation Properties Section)](rotationtype-cell-3-d-rotation-properties-section.md) <br/> |
|RotationXAngle  <br/> |Determines the angle of rotation along the X-axis, in degrees (0.0 - 359.9). |[RotationXAngle Cell (3-D Rotation Properties Section)](rotationxangle-cell-3-d-rotation-properties-section.md) <br/> |
|RotationYAngle  <br/> |Determines the angle of rotation along the Y-axis, in degrees (0.0 - 359.9). |[RotationYAngle Cell (3-D Rotation Properties Section)](rotationyangle-cell-3-d-rotation-properties-section.md) <br/> |
|RotationZAngle  <br/> |Determines the angle of rotation along the Z-axis, in degrees (0.0 - 359.9). |[RotationZAngle Cell (3-D Rotation Properties Section)](rotationzangle-cell-3-d-rotation-properties-section.md) <br/> |
|Rounding  <br/> |Indicates the radius of the rounding arc applied where two contiguous segments of a path meet. For example, rounding can be used to give a rectangle rounded corners. To set rounding, enter a value with units of measure (a number-unit pair). |[Rounding Cell (Line Format Section)](rounding-cell-line-format-section.md) <br/> |
|RouteStyle  <br/> |Determines the routing style and direction for all connectors on the drawing page that don't have a local routing style. |[RouteStyle Cell (Page Layout Section)](routestyle-cell-page-layout-section.md) <br/> |
|ScaleX  <br/> |Specifies the percentage of magnification of the drawing page on the printer page. |[ScaleX Cell (Print Properties Section)](scalex-cell-print-properties-section.md) <br/> |
|ScaleY  <br/> |Specifies the percentage of magnification of the drawing page on the printer page. |[ScaleY Cell (Print Properties Section)](scaley-cell-print-properties-section.md) <br/> |
|SelectMode  <br/> |Determines how you select a group shape and its members. |[SelectMode Cell (Group Properties Section)](selectmode-cell-group-properties-section.md) <br/> |
|ShapeFixedCode Cell  <br/> |Specifies placement behavior for a placeable shape. |[ShapeFixedCode Cell (Shape Layout Section)](shapefixedcode-cell-shape-layout-section.md) <br/> |
|ShapeKeywords  <br/> |Contains search keywords that have been assigned to a master shape. ||
|ShapePermeablePlace  <br/> |Determines whether placeable shapes can be placed on top of a shape when laying out shapes in the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). |[ShapePermeablePlace Cell (Shape Layout Section)](shapepermeableplace-cell-shape-layout-section.md) <br/> |
|ShapePermeableX  <br/> |Determines whether a connector can route horizontally through a placeable shape. |[ShapePermeableX Cell (Shape Layout Section)](shapepermeablex-cell-shape-layout-section.md) <br/> |
|ShapePermeableY  <br/> |Determines whether a connector can route vertically through a shape. |[ShapePermeableY Cell (Shape Layout Section)](shapepermeabley-cell-shape-layout-section.md) <br/> |
|ShapePlaceFlip  <br/> |Determines how a placeable shape flips, rotates, or both on the page when you are laying out shapes by using the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). |[ShapePlaceFlip Cell (Shape Layout Section)](shapeplaceflip-cell-shape-layout-section.md) <br/> |
|ShapePlaceStyle  <br/> |Specifies how shapes are placed on the page when shapes are laid out in the Configure Layout dialog box (on the Design tab, in the Layout group, click Re-Layout Page, and then click More Layout Options). Stores layout style and alignment values from VisCellIndices. |[ShapePlaceStyle Cell (Shape Layout Section)](shapeplacestyle-cell-shape-layout-section.md) <br/> |
|ShapePlowCode  <br/> |Determines whether this placeable shape moves away when you drop another placeable shape near this shape on the drawing page. |[ShapePlowCode Cell (Shape Layout Section)](shapeplowcode-cell-shape-layout-section.md) <br/> |
|ShapeRouteStyle  <br/> |Determines the routing style and direction for a selected connector on the drawing page. |[ShapeRouteStyle Cell (Shape Layout Section)](shaperoutestyle-cell-shape-layout-section.md) <br/> |
|ShapeShdwBlur  <br/> |Determines the size of the blur for a shape's shadow, in points (0.00 to 100.00). |[ShapeShdwBlur Cell (Fill Format Section)](shapeshdwblur-cell-fill-format-section.md) <br/> |
|ShapeShdwObliqueAngle  <br/> |Specifies the angle of oblique direction of a shape's shadow. |[ShapeShdwObliqueAngle Cell (Fill Format Section)](shapeshdwobliqueangle-cell-fill-format-section.md) <br/> |
|ShapeShdwOffsetX  <br/> |Determines the distance in page units that a shape's shadow is offset horizontally from the shape. |[ShapeShdwOffsetX Cell (Fill Format Section)](shapeshdwoffsetx-cell-fill-format-section.md) <br/> |
|ShapeShdwOffsetY  <br/> |Determines the distance in page units that a shape's shadow is offset vertically from the shape. |[ShapeShdwOffsetY Cell (Fill Format Section)](shapeshdwoffsety-cell-fill-format-section.md) <br/> |
|ShapeShdwScaleFactor  <br/> |Specifies the percentage by which the shadow of a shape can be enlarged or reduced. |[ShapeShdwScaleFactor Cell (Fill Format Section)](shapeshdwscalefactor-cell-fill-format-section.md) <br/> |
|ShapeShdwShow  <br/> |Determines whether the shape displays a shadow, as an integer from 0 to 2. |[ShapeShdwShow Cell (Fill Format Section)](shapeshdwshow-cell-fill-format-section.md) <br/> |
|ShapeShdwType  <br/> |Specifies the type of shadow for a shape. |[ShapeShdwType Cell (Fill Format Section)](shapeshdwtype-cell-fill-format-section.md) <br/> |
|ShapeSplit  <br/> |Indicates whether this shape can split shapes that are splittable. |[ShapeSplit Cell (Shape Layout Section)](shapesplit-cell-shape-layout-section.md) <br/> |
|ShapeSplittable  <br/> |Indicates whether this 1-D shape can be split. |[ShapeSplittable Cell (Shape Layout Section)](shapesplittable-cell-shape-layout-section.md) <br/> |
|Sharpen  <br/> |Sharpens a bitmap image. The default value is 0%. Sharpening an image focuses it by increasing the contrast of adjacent pixels. |[Sharpen Cell (Image Properties Section)](sharpen-cell-image-properties-section.md) <br/> |
|ShdwForegnd  <br/> |Determines the color used for the foreground (stroke) of the shape's drop shadow fill pattern. |[ShdwForegnd Cell (Fill Format Section)](shdwforegnd-cell-fill-format-section.md) <br/> |
|ShdwForegndTrans  <br/> |Determines the transparency level for the color used for the foreground (stroke) of the shape's drop shadow fill pattern. |[ShdwForegndTrans Cell (Fill Format Section)](shdwforegndtrans-cell-fill-format-section.md) <br/> |
|ShdwObliqueAngle  <br/> |Contains a number specifying the angle of oblique direction when applying the default page shadow type. |[ShdwObliqueAngle Cell (Page Properties Section)](shdwobliqueangle-cell-page-properties-section.md) <br/> |
|ShdwOffsetX  <br/> |Determines the distance in page units that a shape's drop shadow is offset horizontally from the shape. |[ShdwOffsetX Cell (Page Properties Section)](shdwoffsetx-cell-page-properties-section.md) <br/> |
|ShdwOffsetY  <br/> |Determines the distance in page units that a shape's drop shadow is offset vertically from the shape. |[ShdwOffsetY Cell (Page Properties Section)](shdwoffsety-cell-page-properties-section.md) <br/> |
|ShdwPattern  <br/> |Determines the fill pattern for a shape's shadow. |[ShdwPattern Cell (Fill Format Section)](shdwpattern-cell-fill-format-section.md) <br/> |
|ShdwScaleFactor  <br/> |Specifies the percentage to enlarge or reduce a shape's shadow. |[ShdwScaleFactor Cell (Page Properties Section)](shdwscalefactor-cell-page-properties-section.md) <br/> |
|ShdwType  <br/> |Indicates the default shadow type for a page. |[ShdwType Cell (Page Properties Section)](shdwtype-cell-page-properties-section.md) <br/> |
|SketchAmount  <br/> |Determines the amount of distortion for a sketch effect, as an integer between 0 and 25. |[SketchAmount Cell (Additional Effect Properties Section)](sketchamount-cell-additional-effect-properties-section.md) <br/> |
|SketchEnabled  <br/> |Determines whether a sketch effect is displayed on the shape or not, as a Boolean. |[SketchEnabled Cell (Additional Effect Properties Section)](sketchenabled-cell-additional-effect-properties-section.md) <br/> |
|SketchFillChange  <br/> |Determines the amount of randomization of the shape's fill from the shape's geometry when using a sketch effect, as a percentage of the length of a section. If the value of the SketchFillChange cell is set to 0%, the bounding geometry of a shape's fill matches the shape's geometry. If the value is 100%, the bounding geometry of the shape's fill does not follow the geometry of the shape. |[SketchFillChange Cell (Additional Effect Properties Section)](sketchfillchange-cell-additional-effect-properties-section.md) <br/> |
|SketchLineChange  <br/> |Determines the amount of randomization of the shape's line from the shape's geometry when using a sketch effect, as a percentage of the length of a section. If the value of the SketchLineChange cell is set to 0%, the geometry of the shape's line matches the shape's geometry. If the value is 100%, the geometry of the shape's line does not follow the geometry of the shape. |[SketchLineChange Cell (Additional Effect Properties Section)](sketchlinechange-cell-additional-effect-properties-section.md) <br/> |
|SketchLineWeight  <br/> |Determines the additional thickness added to line weight as the result of a sketch effect, in points from 0 to 50. The thickness of a shape's line increases as the value of the SketchLineWeight cell increases. |[SketchLineWeight Cell (Additional Effect Properties Section)](sketchlineweight-cell-additional-effect-properties-section.md) <br/> |
|SketchSeed  <br/> |Represents a randomization value used to determine the geometry of a sketch effect, as a positive integer. The value of the SketchSeed cell is randomly created when a sketch effect is applied to the shape. |[SketchSeed Cell (Additional Effect Properties Section)](sketchseed-cell-additional-effect-properties-section.md) <br/> |
|SoftEdgesSize  <br/> |Determines the size of a soft edge effect, in points from 0.00 to 100.00. If the SoftEdgesSize cell has a value of 0, the shape does not have soft edges. |[SoftEdgesSize Cell (Additional Effect Properties Section)](softedgessize-cell-additional-effect-properties-section.md) <br/> |
|TextBkgnd  <br/> |Determines the text background color for a shape. |[TextBkgnd Cell (Text Block Format Section)](textbkgnd-cell-text-block-format-section.md) <br/> |
|TextBkgndTrans  <br/> |Determines the transparency level for the background color of the shape's text block. |[TextBkgndTrans Cell (Text Block Format Section)](textbkgndtrans-cell-text-block-format-section.md) <br/> |
|TextDirection  <br/> |Determines the direction of the characters in a text block. |[TextDirection Cell (Text Block Format Section)](textdirection-cell-text-block-format-section.md) <br/> |
|TheData  <br/> |Reserved for future use. |[TheData Cell (Events Section)](thedata-cell-events-section.md) <br/> |
|ThemeIndex  <br/> |Stores the enumeration of the built-in Microsoft Visio theme applied to the document, as an integer. When a new theme is chosen for the document, the ThemeIndex cell for the document and all pages and shapes it contains is updated with the index of the built-in theme. |[ThemeIndex Cell (Theme Properties Section)](themeindex-cell-theme-properties-section.md) <br/> |
|TheText  <br/> |An event cell that is evaluated when a shape's text or text composition changes. |[TheText Cell (Events Section)](thetext-cell-events-section.md) <br/> |
|TopMargin  <br/> |Determines the distance between the top border of the text block and the first line of text it contains. The default is 4.0000 point. This value is independent of the scale of the drawing. If the drawing is scaled, the top margin remains the same. |[TopMargin Cell (Text Block Format Section)](topmargin-cell-text-block-format-section.md) <br/> |
|Transparency  <br/> |Determines the transparency level for a range of a shape's text color. |[Transparency Cell (Character Section)](transparency-cell-character-section.md) <br/> |
|Transparency  <br/> |Determines the transparency level for a layer color. |[Transparency Cell (Image Properties Section)](transparency-cell-image-properties-section.md) <br/> |
|Transparency  <br/> |Determines the transparency level for a layer color. |[Transparency Cell (Layers Section)](transparency-cell-layers-section.md) <br/> |
|TxtAngle  <br/> |Determines the text block's current angle of rotation in relation to the x-axis of the shape. The default is 0 degrees. |[TxtAngle Cell (Text Transform Section)](txtangle-cell-text-transform-section.md) <br/> |
|TxtHeight  <br/> |Determines the height of the text block. The default formula is:= Height \* 1  <br/> |[TxtHeight Cell (Text Transform Section)](txtheight-cell-text-transform-section.md) <br/> |
|TxtLocPinX  <br/> |Determines the x-coordinate of the text block's center of rotation in relation to the origin of the text block. The default formula is:= TxtWidth \* 0.5This formula evaluates to the horizontal center of the text block. |[TxtLocPinX Cell (Text Transform Section)](txtlocpinx-cell-text-transform-section.md) <br/> |
|TxtLocPinY  <br/> |Determines the y-coordinate of the text block's center of rotation relative to the origin of the text block. The default formula is:= TxtHeight \* 0.5  <br/> |[TxtLocPinY Cell (Text Transform Section)](txtlocpiny-cell-text-transform-section.md) <br/> |
|TxtPinX  <br/> |Determines the x-coordinate of the text block's center of rotation in relation to the origin of the shape. The default formula is:= Width \* 0.5  <br/> |[TxtPinX Cell (Text Transform Section)](txtpinx-cell-text-transform-section.md) <br/> |
|TxtPinY  <br/> |Determines the y-coordinate of the text block's center of rotation in relation to the origin of the shape. The default formula is:= Height \* 0.5  <br/> |[TxtPinY Cell (Text Transform Section)](txtpiny-cell-text-transform-section.md) <br/> |
|TxtWidth  <br/> |Determines the width of the text block. The default formula is:= Width \* 1  <br/> |[TxtWidth Cell (Text Transform Section)](txtwidth-cell-text-transform-section.md) <br/> |
|UIVisibility  <br/> |Determines whether the page name is exposed in the user interface (UI). |[UIVisibility Cell (Page Properties Section)](uivisibility-cell-page-properties-section.md) <br/> |
|UpdateAlignBox  <br/> |Recalculates the selection rectangle whenever a control handle is moved. |[UpdateAlignBox Cell (Miscellaneous Section)](updatealignbox-cell-miscellaneous-section.md) <br/> |
|UseGroupGradient  <br/> |Determines whether the shape takes on a gradient when the shape is grouped together with other shapes, as a Boolean. The value of UseGroupGradient cell affects the shape fill only. |[UseGroupGradient Cell (Gradient Properties Section)](usegroupgradient-cell-gradient-properties-section.md) <br/> |
|VariationColorIndex  <br/> |Determines the color index of the active theme variation on the page, as an integer. |[VariationColorIndex Cell (Theme Properties Section)](variationcolorindex-cell-theme-properties-section.md) <br/> |
|VariationStyleIndex  <br/> |Determines the style index of the active theme variation on the page, as an integer. |[VariationStyleIndex Cell (Theme Properties Section)](variationstyleindex-cell-theme-properties-section.md) <br/> |
|VerticalAlign  <br/> |Determines the vertical alignment of text within the text block. |[VerticalAlign Cell (Text Block Format Section)](verticalalign-cell-text-block-format-section.md) <br/> |
|ViewMarkup  <br/> |Determines whether markup appears in the drawing window. |[ViewMarkup Cell (Document Properties Section)](viewmarkup-cell-document-properties-section.md) <br/> |
|WalkPreference  <br/> |Determines whether an endpoint of a 1-D shape moves to a horizontal or vertical connection point on the shape it is glued to, using dynamic glue, when the shape is moved to an ambiguous position. By default, both endpoints of the 1-D shape move to horizontal connection points. |[WalkPreference Cell (Glue Info Section)](walkpreference-cell-glue-info-section.md) <br/> |
|Width  <br/> |Contains the width of the selected shape in drawing units. The default formula for determining the width of a 1-D shape is:= SQRT((EndX - BeginX) ^ 2 + (EndY - BeginY) ^ 2)  <br/> |[Width Cell (Shape Transform Section)](width-cell-shape-transform-section.md) <br/> |
|XGridDensity  <br/> |Specifies the type of horizontal grid to use. |[XGridDensity Cell (Ruler &amp; Grid Section)](xgriddensity-cell-rulergrid-section.md) <br/> |
|XGridOrigin  <br/> |Specifies the horizontal coordinate of the grid origin. |[XGridOrigin Cell (Ruler &amp; Grid Section)](xgridorigin-cell-rulergrid-section.md) <br/> |
|XGridSpacing  <br/> |Specifies the distance between horizontal lines in a fixed grid (XGridDensity = 0). |[XGridSpacing Cell (Ruler &amp; Grid Section)](xgridspacing-cell-rulergrid-section.md) <br/> |
|XRulerDensity  <br/> |Specifies the horizontal subdivisions on the ruler for the page. |[XRulerDensity Cell (Ruler &amp; Grid Section)](xrulerdensity-cell-rulergrid-section.md) <br/> |
|XRulerOrigin  <br/> |Specifies the zero point on the x-axis ruler for the page. |[XRulerOrigin Cell (Ruler &amp; Grid Section)](xrulerorigin-cell-rulergrid-section.md) <br/> |
|YGridDensity  <br/> |Specifies the type of vertical grid to use. |[YGridDensity Cell (Ruler &amp; Grid Section)](ygriddensity-cell-rulergrid-section.md) <br/> |
|YGridOrigin  <br/> |Specifies the vertical origin of the grid. |[YGridOrigin Cell (Ruler &amp; Grid Section)](ygridorigin-cell-rulergrid-section.md) <br/> |
|YGridSpacing  <br/> |Specifies the distance between vertical lines in a fixed grid (YGridDensity = 0). |[YGridSpacing Cell (Ruler &amp; Grid Section)](ygridspacing-cell-rulergrid-section.md) <br/> |
|YRulerDensity  <br/> |Specifies the vertical subdivisions on the ruler for the page. |[YRulerDensity Cell (Ruler &amp; Grid Section)](yrulerdensity-cell-rulergrid-section.md) <br/> |
|YRulerOrigin  <br/> |Specifies the zero point on the y-axis ruler for the page. |[YRulerOrigin Cell (Ruler &amp; Grid Section)](yrulerorigin-cell-rulergrid-section.md) <br/> |
   

