---
title: Shape Append Clause
TOCTitle: Shape Append Clause
ms:assetid: 8f29afc3-fb93-4439-b67b-cad0eed0bda9
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/JJ249633(v=office.15)
ms:contentKeyID: 48546301
ms.date: 09/18/2015
mtps_version: v=office.15
---

# Shape Append Clause


**Applies to**: Access 2013 | Office 2013

**In this article**  
Syntax  
Description  
Remarks  
Remarks  

The shape command APPEND clause appends a column or columns to a **Recordset**. Often these columns are chapter columns, which refer to a child **Recordset**.

## Syntax

``` 
 
SHAPE [parent-command [[AS] parent-alias]] APPEND column-list
```

## Description

The parts of this clause are as follows:

  - *parent-command*

  - Zero or one of the following (you may omit the *parent-command* entirely):
    
      - A provider command within curly braces ("{}") that returns a **Recordset** object. The command is issued to the underlying data provider, and its syntax depends on the requirements of that provider. This will typically be the SQL language, although ADO does not require any particular query language.
    
      - Another shape command embedded in parentheses.
    
      - The TABLE keyword, followed by the name of a table in the data provider.

  - *parent-alias*

  - An optional alias that refers to the parent **Recordset**.

  - *column-list*

  - One or more of the following:
    
      - An aggregate column.
    
      - A calculated column.
    
      - A new column created with the NEW clause.
    
      - A chapter column. A chapter column definition is enclosed in parentheses ("()"). See syntax below:

<!-- end list -->

``` 
 
SHAPE [parent-command [[AS] parent-alias]] 
 APPEND (child-recordset [ [[AS] child-alias] 
 RELATE parent-column TO child-column | PARAMETER param-number, ... ]) 
 [[AS] chapter-alias] 
 [, ... ] 
```

  - *child-recordset*

  - 
    
      - A provider command within curly braces ("{}") that returns a **Recordset** object. The command is issued to the underlying data provider, and its syntax depends on the requirements of that provider. This will typically be the SQL language, although ADO does not require any particular query language.
    
      - Another shape command embedded in parentheses.
    
      - The name of an existing shaped **Recordset**.
    
      - The TABLE keyword, followed by the name of a table in the data provider.

  - *child-alias*

  - An alias that refers to the child **Recordset**.

  - *parent-column*

  - A column in the **Recordset** returned by the *parent-command.*

  - *child-column*

  - A column in the **Recordset** returned by the *child-command*.

  - *param-number*

  - See [Operation of Parameterized Commands](operation-of-parameterized-commands.md).

  - *chapter-alias*

  - An alias that refers to the chapter column appended to the parent.


> [!NOTE]
> <P>The <EM>"parent-column</EM> TO <EM>child-column"</EM> clause is actually a list, where each relation defined is separated by a comma.</P>




> [!NOTE]
> <P>The clause after the APPEND keyword is actually a list, where each clause is separated by a comma and defines another column to be appended to the parent.</P>



## Remarks

When you construct provider commands from user input as part of a SHAPE command, SHAPE will treat the user-supplied a provider command as an opaque string and pass them faithfully to the provider. For example, in the following SHAPE command,

``` 
 
SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2) 
```

SHAPE will execute two commands: select \* from t1 and (select \* from t2 RELATE k1 TO k2). If the user supplies a compound command consisting of multiple provider commands separated by semicolons, SHAPE is not able to discern the difference. So in the following SHAPE command,

``` 
 
SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2) 
```

SHAPE executes select \* from t1; drop table t1 and (select \* from t2 RELATE k1 TO k2), not realizing that drop table t1 is a separate and in this case, dangerous, provider command. Applications must always validate the user input to prevent such potential hacker attacks from happening.

## Remarks

When you construct provider commands from user input as part of a SHAPE command, SHAPE will treat the user-supplied a provider command as an opaque string and pass them faithfully to the provider. For example, in the following SHAPE command,

``` 
 
SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2) 
```

SHAPE will execute two commands: select \* from t1 and (select \* from t2 RELATE k1 TO k2). If the user supplies a compound command consisting of multiple provider commands separated by semicolons, SHAPE is not able to discern the difference. So in the following SHAPE command,

``` 
 
SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2) 
```

SHAPE executes select \* from t1; drop table t1 and (select \* from t2 RELATE k1 TO k2), not realizing that drop table t1 is a separate and in this case, dangerous, provider command. Applications must always validate the user input to prevent such potential hacker attacks from happening.

