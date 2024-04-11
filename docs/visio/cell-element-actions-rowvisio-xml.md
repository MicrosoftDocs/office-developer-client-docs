---
title: "Cell element (Actions Row) (Visio XML)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 5ae2b4db-03f4-1b8a-1274-7eb1521f2f59
description: "Specifies one property of an action associated with a custom command on a shortcut or action tag menu."
---

# Cell element (Actions Row) (Visio XML)

Specifies one property of an action associated with a custom command on a shortcut or action tag menu.
  
## Element information

||Value |
|:-----|:-----|
|**Element type** <br/> |[Cell_Type](cell_type-complextypevisio-xml.md) <br/> |
|**Namespace** <br/> |http://schemas.microsoft.com/office/visio/2012/main  <br/> |
|**Schema file** <br/> |VisioSchema15.xsd  <br/> |
|**Document parts** <br/> |masters.xml, master#.xml, pages.xml, page#.xml  <br/> |
   
## Definition

```XML
< xs:element name="Cell" type="Cell_Type" minOccurs="0" maxOccurs="unbounded" >
</xs:element >
```

## Elements and attributes

If the schema defines specific requirements, such as **sequence**, **minOccurs**, **maxOccurs**, and **choice**, see the definition section. 
  
### Parent elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[Row element (Actions Section)](row-element-actions-sectionvisio-xml.md) <br/> |[ActionsRow_Type](actionsrow_type-complextypevisio-xml.md) <br/> |Specifies one property of an action associated with a custom command on a shortcut or action tag menu. |
   
### Child elements

|**Element**|**Type**|**Description**|
|:-----|:-----|:-----|
|[RefBy](refby-element-cell_type-complextypevisio-xml.md) <br/> |[RefBy_Type](refby_type-complextypevisio-xml.md) <br/> |Specifies a reference to a drawing page. |
   
### Attributes

|**Attribute**|**Type**|**Required**|**Description**|**Possible values**|
|:-----|:-----|:-----|:-----|:-----|
|E  <br/> |xsd:string  <br/> |optional  <br/> |Indicates that the formula evaluates to an error. The value of **E** is the current value (an error message string); the value of the **V** attribute is the last valid value. |An error message string. |
|F  <br/> |xsd:string  <br/> |optional  <br/> | Represents the element's formula. This attribute can contain one of the following strings:  <br/>  '(some formula)' if the formula exists locally  <br/> `No Formula` if the formula is locally deleted or blocked  <br/> `Inh` if the formula is inherited. |A formula. |
|N  <br/> |xsd:string  <br/> |required  <br/> |Represents the name of the ShapeSheet cell. |The name of the ShapeSheet cell. See the Remarks section below. |
|U  <br/> |xsd:string  <br/> |optional  <br/> |Represents a unit of measure The default is DL. |The units of the cell. |
|V  <br/> |xsd:string  <br/> |optional  <br/> |Represents the value of the cell. |The value of the ShapeSheet cell. |
   
## Remarks

The **N** attribute of this **Cell** element must be one of a limited set of values that correspond to ShapeSheet cells. Refer to the table below to determine the values of the **N** attribute that are permitted for this **Cell** element. 
  
|**Value**|**Description**|**More information**|
|:-----|:-----|:-----|
|Action  <br/> |Contains the formula to be executed when a user chooses a command on a shortcut or action tag menu. |[Action Cell (Actions Section)](action-cell-actions-section.md) <br/> |
|BeginGroup  <br/> |Indicates whether a separator is inserted into the menu above this action. |[BeginGroup Cell (Actions Section)](begingroup-cell-actions-section.md) <br/> |
|ButtonFace  <br/> |Identifies the icon that appears next to an item on a shortcut or action tag menu. |[ButtonFace Cell (Actions Section)](buttonface-cell-actions-section.md) <br/> |
|Checked  <br/> |Indicates whether an item is checked on the shortcut or action tag menu. |[Checked Cell (Actions Section)](checked-cell-actions-section.md) <br/> |
|Disabled  <br/> |Indicates whether an item on a shortcut or action tag menu is disabled. |[Disabled Cell (Actions Section)](disabled-cell-actions-section.md) <br/> |
|FlyoutChild  <br/> |Determines whether the row is a child flyout menu of the last row above it that is not a flyout child. |[FlyoutChild Cell (Actions Section)](flyoutchild-cell-actions-section.md) <br/> |
|Invisible  <br/> |Indicates whether the action is visible on the action tag or shortcut menu. |[Invisible Cell (Actions Section)](invisible-cell-actions-section.md) <br/> |
|Menu  <br/> |Defines the name of a menu item that appears on a shortcut or action tag menu for a shape or page. |[Menu Cell (Actions Section)](menu-cell-actions-section.md) <br/> |
|ReadOnly  <br/> |Controls whether the action on an action tag or shortcut menu is read-only. |[ReadOnly Cell (Actions Section)](readonly-cell-actions-section.md) <br/> |
|SortKey  <br/> |A number that determines the order of actions that appear on a shortcut or action tag menu. |[SortKey Cell (Actions Section) SortKey Cell (Actions Section)](sortkey-cell-actions-section.md) <br/> |
|TagName  <br/> |Contains the name of the action tag that this action is associated with. |[TagName Cell (Actions Section)](tagname-cell-actions-section.md) <br/> |
   

