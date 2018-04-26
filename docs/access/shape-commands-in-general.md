---
title: "Shape Commands in General"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
  
localization_priority: Normal
ms.assetid: ad555aa7-bc64-b495-a98d-e927061a5809
description: "Data shaping defines the columns of a shaped Recordset , the relationships between the entities represented by the columns, and the manner in which the Recordset is populated with data."
---

# Shape Commands in General

Data shaping defines the columns of a shaped **Recordset**, the relationships between the entities represented by the columns, and the manner in which the **Recordset** is populated with data. 
  
A shaped **Recordset** may consist of the following types of columns. 
  
|**Column type**|**Description**|
|:-----|:-----|
|data  <br/> |Fields from a **Recordset** returned by a query command to a data provider, table, or previously shaped **Recordset**.  <br/> |
|chapter  <br/> |A reference to another **Recordset**, called a  *chapter*  . Chapter columns make it possible to define a  *parent-child*  relationship where the  *parent*  is the **Recordset** containing the chapter column and the  *child*  is the **Recordset** represented by the chapter.  <br/> |
|aggregate  <br/> |The value of the column is derived by executing an  *aggregate function*  on all the rows or a column of all the rows of a child **Recordset**. (See Aggregate Functions in the following topic, [Aggregate Functions, the CALC Function, and the NEW Keyword](aggregate-functions-the-calc-function-and-the-new-keyword.md).)  <br/> |
|calculated expression  <br/> |The value of the column is derived by calculating a Visual Basic for Applications expression on columns in the same row of the **Recordset**. The expression is the argument to the CALC function. (See Calculated Expression in the following topic, [Aggregate Functions, the CALC Function, and the NEW Keyword](aggregate-functions-the-calc-function-and-the-new-keyword.md) and in [Visual Basic for Applications Functions](visual-basic-for-applications-functions.md).)  <br/> |
|new  <br/> |Empty, fabricated fields, which may be populated with data at a later time. The column is defined with the NEW keyword. (See NEW keyword in the following topic, [Aggregate Functions, the CALC Function, and the NEW Keyword](aggregate-functions-the-calc-function-and-the-new-keyword.md).)  <br/> |
   
A shape command may contain a clause specifying a query command to an underlying data provider that will return a **Recordset** object. The query's syntax depends on the requirements of the underlying data provider. This will usually be Structured Query Language (SQL), although ADO does not require the use of any particular query language. 
  
You could use a SQL JOIN clause to relate two tables; however, a hierarchical **Recordset** may represent the information more efficiently. Each row of a **Recordset** created by a JOIN repeats information redundantly from one of the tables. A hierarchical **Recordset** has only one parent **Recordset** for each of multiple child **Recordset** objects. 
  
Shape commands can be issued by **Recordset** objects or by setting the [CommandText](commandtext-property-ado.md) property of the [Command](command-object-ado.md) object and then calling the [Execute](http://msdn.microsoft.com/library/01812c8c-403e-4428-23f6-86bda747bd0e%28Office.15%29.aspx) method. 
  
Shape commands can be nested. That is, the  *parent-command*  or  *child-command*  may itself be another shape command. 
  
The shape provider always returns a client cursor, even when the user specifies a cursor location of **adUseServer**. 
  
For information about navigating a hierarchical **Recordset**, see [Accessing Rows in a Hierarchical Recordset](accessing-rows-in-a-hierarchical-recordset.md).
  
For precise information about syntactically correct shape commands, see [Formal Shape Grammar](formal-shape-grammar.md).
  

