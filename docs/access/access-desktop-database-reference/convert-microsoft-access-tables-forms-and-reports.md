---
title: Convert Microsoft Access Tables, Forms, and Reports
TOCTitle: Convert Microsoft Access Tables, Forms, and Reports
ms:assetid: cc170e62-a663-60e8-4446-07a7a874b747
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Ff834413(v=office.15)
ms:contentKeyID: 48547731
ms.date: 09/18/2015
mtps_version: v=office.15
f1_keywords:
- vbaac10.chm5187104
f1_categories:
- Office.Version=v15
---

# Convert Microsoft Access Tables, Forms, and Reports


_**Applies to:** Access 2013 | Office 2013_

**In this article**  
Indexes and Relationships  
The LimitToList Property of Combo Boxes  
Menus and In-Place Activation of OLE Objects  
Referencing a Control on a Read-Only Form  
Date Fields and Data Entry  
Buttons Created with the Command Button Wizard  
Form and Report Class Modules  
Converted Version 2.0 Report Has Different Margins  
Can't Use the Format Property to Distinguish Null Values and Zero-Length Strings  

Several changes introduced by Microsoft Access 2002 might affect the behavior of your version 1.*x* or 2.0 applications. The following sections provide more information about those changes.

## Indexes and Relationships

A Microsoft Access table can contain up to 32 indexes. Very complex tables that are a part of many relationships may exceed the index limit, and you won't be able to convert the database that contains these tables. The Microsoft Access database engine creates indexes on both sides of relationships between tables. If your database won't convert, delete some relationships and try again to convert the database.

## The LimitToList Property of Combo Boxes

In Microsoft Access 2002 or later, combo boxes accept **Null** values when the **LimitToList** property is set to **True** (–1), whether or not the list contains **Null** values. In version 2.0, a combo box that has the **LimitToList** property set to **True** won't accept a **Null** value unless the list contains a **Null** value. If you want to prevent users from entering a **Null** value by using a combo box, set the **Required** property of the field in the table to **Yes**.

## Menus and In-Place Activation of OLE Objects

In order to make additional functionality available to you while activating OLE objects in place, some menu commands may have been moved to a menu that isn't replaced when you activate an OLE server.

Macros in your converted application that use a DoMenuItem action to carry out a version 2.0 menu command when a component is activated won't be affected by the changes. Version 2.0 commands are mapped to their equivalents in later versions of Microsoft Access.

## Referencing a Control on a Read-Only Form

In Microsoft Access 2002 or later, you can't use an expression to refer to the value of a control on a read-only form that's bound to an empty record source. In previous versions, the expression returns a **Null** value. Before you reference a control on a read-only form, you should make sure that the form's record source contains records.

## Date Fields and Data Entry

If you enter **3/3** in a field of type Date on a form or a table datasheet, the current year is automatically added in Microsoft Access 2002 or later. However, if you enter **3/3/** in the same field, Microsoft Access returns an error message. You must omit the last date delimiter so that Microsoft Access can translate the date into the proper format.

## Buttons Created with the Command Button Wizard

If you used the Command Button Wizard in version 2.0 or 7.0 of Microsoft Access to generate code that called another application, you should delete the button and re-create it by using the Command Button Wizard in Microsoft Access 2002 or later.

## Form and Report Class Modules

In versions of Microsoft Access prior to 2002, **Form** and **Report** objects have associated class modules even if there's no code behind the object. In Microsoft Access 2002 or later, you can set a form's or report's **HasModule** property to **False**. When you set the **HasModule** property to **False**, the form or report will take up less disk space and will load faster because it will no longer have an associated class module.

## Converted Version 2.0 Report Has Different Margins

You may encounter problems when trying to print or preview a report in Microsoft Access 2002 or later that has been converted from Microsoft Access 2.0 if the report has some margins set to 0. When you convert a Microsoft Access 2.0 report, margins aren't set to 0; they are instead set to the minimum margin that's valid for the default printer. This prevents the report from printing data in the unprintable region of the printer.

To resolve this problem, reduce the column width, column spacing, or number of columns in the report so that the width of the columns plus the width of the default margins is equal to or less than the width of your paper.

## Can't Use the Format Property to Distinguish Null Values and Zero-Length Strings

In versions 1.*x* and 2.0, you can use the **Format** property of a control to display different values for **Null** values and zero-length strings (" "). In Microsoft Access 2002 or later, to distinguish between **Null** values and zero-length strings in a control on a form, set the control's **ControlSource** property to an expression that tests for the **Null** value case. For example, to display "Null" or "ZLS" in a control, set its **ControlSource** property to the following expression:

\=IIf(IsNull(\[MyControl\]), "Null", Format(\[MyControl\], "@;ZLS"))

