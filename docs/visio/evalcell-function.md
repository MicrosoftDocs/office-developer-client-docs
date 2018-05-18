---
title: "EVALCELL Function"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: 4aa3a1c9-dec9-5eb0-5743-0534c0b3bb5f
description: "Takes a reference to a cell that contains a custom function as well as one or more name-value pairs to pass to the custom function as arguments (optional). Returns the calculated result of the custom function given the specified arguments and values."
---

# EVALCELL Function

Takes a reference to a cell that contains a custom function as well as one or more name-value pairs to pass to the custom function as arguments (optional). Returns the calculated result of the custom function given the specified arguments and values.
  
## Syntax

EVALCELL( ** *cellRef* **,[ ** *arg1Name,arg1* ** ],[ ** *arg2Name,arg2* ** ],…) 
  
### Parameters

|**Name**|**Required/Optional**|**Data Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _cellRef_ <br/> |Required  <br/> |**String** <br/> |A reference to the cell that contains the custom function. Cross-sheet references are allowed.  <br/> |
| _arg1Name_ <br/> |Optional  <br/> |**String** <br/> |The name of the first argument to be passed to the custom function. Spaces are allowed.  <br/> |
| _arg1_ <br/> |Optional  <br/> |**Varies** <br/> |Value of the  _arg1_ parameter.  <br/> |
| _arg2Name_ <br/> |Optional  <br/> |**String** <br/> |The name of the second argument to be passed to the custom function. Spaces are allowed.  <br/> |
| _arg2_ <br/> |Optional  <br/> |**Varies** <br/> |Value of the  _arg2_ parameter.  <br/> |
   
### Return Value

Number
  
## Remarks

The calling cell does not have to specify every argument used by the custom function. 
  
## Example

The following example shows how to use the EVALCELL function in conjunction with the ARG function to find the middle value from a set of three values. 
  
In the expression cell, place the following code that defines the custom function: 
  
```vb
User.MiddleValue = IF(ARG("A")>ARG("B"),IF(ARG("B")>ARG("C"),ARG("B"),IF(ARG("A")>ARG("C"),ARG("C"),ARG("A"))),IF(ARG("A")>ARG("C"),ARG("A"),IF(ARG("B")>ARG("C"),ARG("C"),ARG("B"))))
```

In the calling cells, place the following code that calls the custom function:
  
```vb
User.Middle1 = EVALCELL(User.MiddleValue,"A",3,"B",9,"C",5) 
User.Middle2 = EVALCELL(User.MiddleValue,"A",12,"B",0,"C",21) 

```


