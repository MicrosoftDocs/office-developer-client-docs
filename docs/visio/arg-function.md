---
title: "ARG Function"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
 
ms.localizationpriority: medium
ms.assetid: 781369e1-fade-ec10-7c51-0f921b5c3b76
description: "Specifies an argument that the calling cell can pass to a custom function, as well as the default value returned by the custom function if the calling cell does not pass in a value for the argument. Returns the value specified by the calling cell and the matching argName parameter."
---

# ARG Function

Specifies an argument that the calling cell can pass to a custom function, as well as the default value returned by the custom function if the calling cell does not pass in a value for the argument. Returns the value specified by the calling cell and the matching argName parameter.
  
## Syntax

ARG(***argName***,[ ***defaultValue*** ]) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _argName_ <br/> |Required  <br/> |**String** <br/> |The name of an argument that the calling cell can pass into the function. |
| _default Value_ <br/> |Optional  <br/> |**Numeric** <br/> |The value returned by ARG if the calling cell did not pass in a value for the  _argName_ parameter. |
   
## Remarks

As a shape developer, you can create custom functions by placing an expression in one cell and calling that expression from one or more other cells. The expression can include literal strings, ShapeSheet functions, and cell references. The expression can also include specific arguments that are passed in by the calling cell. 
  
The calling cell specifies the cell that contains the custom function as well as any arguments that it wants to pass to the function. The expression cell is evaluated and the result returned to the calling cell.
  
## Example

The following example shows how to use the ARG function in conjunction with the EVALCELL function to find the middle value from a set of three values. 
  
In the expression cell, place the following code that defines the custom function: 
  
```vb
User.MiddleValue = IF(ARG("A")>ARG("B"),IF(ARG("B")>ARG("C"),ARG("B"),IF(ARG("A")>ARG("C"),ARG("C"),ARG("A"))),IF(ARG("A")>ARG("C"),ARG("A"),IF(ARG("B")>ARG("C"),ARG("C"),ARG("B"))))
```

In the calling cells, place the following code that calls the custom function:
  
```vb
User.Middle1 = EVALCELL(User.MiddleValue,"A",3,"B",9,"C",5) 
User.Middle2 = EVALCELL(User.MiddleValue,"A",12,"B",0,"C",21) 

```


