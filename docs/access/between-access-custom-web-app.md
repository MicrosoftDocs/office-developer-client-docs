---
title: "BETWEEN (Access custom web app)"
  
  
manager: kelbow
ms.date: 09/05/2017
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 9dcb32c6-ed9b-4a09-9e6a-48cc50063a6f
description: "Specifies a range to test."
---

# BETWEEN (Access custom web app)

Specifies a range to test.
  
> [!IMPORTANT]
> Microsoft no longer recommends creating and using Access web apps in SharePoint. As an alternative, consider using [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/) to build no-code business solutions for the web and mobile devices. 
  
## Syntax

 *test_expression*  [ NOT ] **BETWEEN** *begin_expression* **AND** *end_expression* 
  
The **Between** operator contains the following arguments. 
  
|**Argument**|**Required**|**Description**|
|:-----|:-----|:-----|
| *test_expression*  <br/> |Yes  <br/> |The expression to test for in the range defined by  *begin_expression*  and  *end_expression*  . Must be the same data type as both  *begin_expression*  and  *end_expression*  .  <br/> |
| *NOT*  <br/> |No  <br/> |Specifies that the result of the predicate be negated.  <br/> |
| *begin_expression*  <br/> |Yes  <br/> |A valid expression. Must be the same data type as both  *test_expression*  and  *end_expression*  .  <br/> |
| *end_expression*  <br/> |Yes  <br/> |A valid expression. Must be the same data type as both  *test_expression*  and  *begin_expression*  .  <br/> |
| *AND*  <br/> |Yes  <br/> |Indicates  *test_expression*  should be within the range indicated by  *begin_expression*  and  *end_expression*  .  <br/> |
   
## Result Type

 **Boolean**
  
## Remarks

 **BETWEEN** returns **TRUE** if the value of  *test_expression*  is greater than or equal to the value of  *begin_expression*  and less than or equal to the value of  *end_expression*  . 
  
 **NOT BETWEEN** returns **TRUE** if the value of  *test_expression*  is less than the value of  *begin_expression*  or greater than the value of  *end_expression*  . 
  
To specify an exclusive range, use the greater than (\>) and less than operators (\<).
  

