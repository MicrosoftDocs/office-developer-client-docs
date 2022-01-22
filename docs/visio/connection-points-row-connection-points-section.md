---
title: "Connection Points Row (Connection Points Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm3005
 
ms.localizationpriority: medium
ms.assetid: eaac62a5-f516-9b81-587a-8e0e02de59ee
description: "Contains the x - and y -coordinates, horizontal and vertical direction, and type for a single connection point on a shape. Coordinates of connection points are measured from the origin of the shape. A shape contains one Connection Points row for each connection point."
---

# Connection Points Row (Connection Points Section)

Contains the  *x*  - and  *y*  -coordinates, horizontal and vertical direction, and type for a single connection point on a shape. Coordinates of connection points are measured from the origin of the shape. A shape contains one Connection Points row for each connection point. 
  
If Connection Points rows are named, those names appear as Connections. *name*  in the ShapeSheet window. Connection Points rows contain the following cells. For more details, see the specific cell topics. 
  
|**Cell**|**Description**|
|:-----|:-----|
|[X](x-cell-connection-points-section.md) <br/> |The *x*  -coordinate for a connection point in local coordinates.  <br/> |
|[Y](y-cell-connection-points-section.md) <br/> |The *y*  -coordinate for a connection point in local coordinates.  <br/> |
|[DirX/A](dirxa-cell-connection-points-section.md) <br/> |The *x*  -component for the required alignment vector of a matching connection point. It is also used to orient the attached leg of a dynamic connector. This cell takes a floating point value.  <br/> |
|[DirY/B](diryb-cell-connection-points-section.md) <br/> |The *y*  -component for the required alignment vector of a matching connection point. It is also used to orient the attached leg of a dynamic connector. This cell takes a floating point value.  <br/> |
|[Type/C](typec-cell-connection-points-section.md) <br/> |The connection point type (0 = inward; 1 = outward; 2 = inward + outward).  <br/> |
|[D](d-cell-connection-points-section.md) <br/> |A scratch cell that you can use for entering or testing formulas. To access this cell, right-click a row, and then click **Change Row Type** on the shortcut menu.  <br/> |
   
## Remarks

Cells in the Connections. *name*  row are labeled DirX/A, DirY/B, and Type/C because these rows can be extended or non-extended rows. 
  
Most connection points (all connection points created through the user interface) are non-extended and have DirX, DirY, and Type cells. Their row type is **visTagCnnctPt** or **visTagCnnctNamed.**
  
In non-extended rows the DirX and DirY cells together define a direction vector that influences the rotation of shapes involved in connections using the connection point. If both are zero the point is directionless. Connection points are of the following types:
  
- Inward (0), which means that shapes glue to them. This is the default.
    
- Outward (1), which means these connection points will glue to inward connection points.
    
- Both inward and outward (2), in which case the direction is the inward direction, which is reversed if used as an outward connection.
    
Extended rows have A, B, C, and D cells and behave like directionless non-extended rows of type Inward. Extended rows are not commonly used, but you might use them to associate data with a connection point in the A, B, C, and D cells. Their row type is **visTagCnnctPtABCD** or **visTagCnnctNamedABCD**. Extended rows can be identified by the presence of a formula in the D cell. 
  
 You can add as many Connections.  *name*  rows as you need, assign meaningful names to the rows, and set cell values. To add a connection point to an existing Connection Points section, right-click a row and click **Insert Row** on the shortcut menu. 
  
You can reference Connection Points row cells by their row name, which appears in a ShapeSheet window in red text. To change the row name, click it, and then type a name such as  *Custom*  , for example, to create the row name Connections.Custom. You can then reference the X cell using Connections.Custom.X, for example, or Connections.X1 if you want to use the row number. 
  
The row name you enter must be unique within the section. When you create a name for one row in the Connection Points section, Microsoft Office Visio names all the rows in the section with the default name, Connections.Row_ *n*  . 
  
Named Connection Points rows are not compatible with versions of Visio earlier than 5.0. When saving a Visio drawing file with named Connection Points rows to an earlier format, references to named Connection Points rows are converted to indexed references, and the row names are lost.
  

