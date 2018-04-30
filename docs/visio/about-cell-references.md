---
title: "About Cell References"
ms.author: null
author: null
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82251827
ms.prod: null
localization_priority: Normal
ms.assetid: e6a9aceb-90d7-fb53-eaf4-416a1ae2a98b
description: "You can create interdependencies among formulas by means of ShapeSheet cell references. Cell references give you the power to calculate a value for one cell based on another cell's value. For example, a shape's Width cell might contain a formula that calculates the shape's width by referring to the value of its Height cell, so that when a user resizes the shape vertically, its width stays in proportion."
---

# About Cell References

You can create interdependencies among formulas by means of ShapeSheet cell references. Cell references give you the power to calculate a value for one cell based on another cell's value. For example, a shape's Width cell might contain a formula that calculates the shape's width by referring to the value of its Height cell, so that when a user resizes the shape vertically, its width stays in proportion.
  
In a cell's formula, you can refer to a cell of the same shape or another object, such as a document or page, so that Microsoft Visio calculates a value for one cell based on another cell's value.
  
## What cell references can include

Cell references can include shape identifiers (IDs) or names. You can always refer to any shape on the page by its ID, whether the shape is named or not. If a shape hasn't been named, its default name is Sheet. *i*  , where  *i*  is the shape ID. The ID is assigned when the shape is created and does not change unless you move the shape to another page or document. If more than one shape on a page has the same name, you must include the assigned ID. 
  
## Cell reference syntax and examples

The syntax you use and whether you can refer to a shape by name depend on the relationship between the two objects. These general rules apply:
  
- If a shape is a peer of the shape whose formula you are editing, you can refer to the peer shape by name. If the peer shape is a group, you can refer by name to the group, but not its members. Neither can you refer by name to a shape's parent or its parent's peers.
    
- You can use Sheet.ID syntax to refer to any shape on the page, whether the shape is in a group or is a parent of a shape.
    
- Names that contain nonstandard characters must be enclosed in single quotation marks. Single quotation mark characters in a nonstandard name must be prefixed by a single quotation mark.
    
|**To reference a cell of**|**Use this syntax**|**Example**|
|:-----|:-----|:-----|
|The same shape  <br/> | CellName  <br/> | Width  <br/> |
| A shape, group, or guide  <br/> | Shapename!CellName  <br/> | Star!Angle  <br/> |
| A shape, group, or guide in which more than one shape at the same level has the same name  <br/> | Shapename.ID!CellName  <br/> | Executive.2!Height  <br/> |
| A named column with indexed rows  <br/> | Section.Column[index]  <br/> | Char.Font[3]  <br/> |
| An unnamed column with indexed rows  <br/> | Section.ColumnIndex  <br/> | Scratch.A5  <br/> |
| Any shape, page, master, or style  <br/> | Sheet.ID!CellName  <br/> | Sheet.8!FillForegnd  <br/> |
| A master  <br/> | Masters[MasterName]!SheetName!CellReference  <br/> | Masters[Gear]!Shaft!Geometry1.X1  <br/> |
| The page or master page on which the object is located  <br/> | ThePage!CellReference  <br/> | ThePage!User.Vanishing_Point  <br/> |
| Another page in the document  <br/> | Pages[PageName]!SheetName!CellReference  <br/> | Pages[Page-3]!Sheet.4!BeginX  <br/> |
| A style  <br/> | Styles!SheetName!CellReference  <br/> | Styles!Manager!LineColor  <br/> |
| The document  <br/> | TheDoc!CellReference  <br/> | TheDoc!PreviewQuality  <br/> |
| A shape, page, master, document, or style with a nonstandard name.  <br/> | 'Sheetname'!CellName  <br/> | '1-D'!LineColor  <br/> |
   

