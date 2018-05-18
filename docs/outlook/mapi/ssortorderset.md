---
title: "SSortOrderSet"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SSortOrderSet
api_type:
- COM
ms.assetid: e7f9be6a-92e7-44a8-93ee-b087713a31df
description: "Last modified: March 09, 2015"
---

# SSortOrderSet

  
  
**Applies to**: Outlook 
  
Defines a collection of sort keys for a table that is used for standard or categorized sorting.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[CbNewSSortOrderSet](cbnewssortorderset.md), [CbSSortOrderSet](cbssortorderset.md), [SizedSSortOrderSet](sizedssortorderset.md) <br/> |
   
```cpp
typedef struct _SSortOrderSet
{
  ULONG cSorts;
  ULONG cCategories;
  ULONG cExpanded;
  SSortOrder aSort[MAPI_DIM];
} SSortOrderSet, FAR *LPSSortOrderSet;

```

## Members

 **cSorts**
  
> Count of [SSortOrder](ssortorder.md) structures that are included in the **aSort** member. 
    
 **cCategories**
  
> Count of columns that are designated as category columns. Possible values range from zero, which indicates a non-categorized or standard sort, to the number indicated by the **cSorts** member. 
    
 **cExpanded**
  
> Count of categories that start in an expanded state, where all of the rows that apply to the category are visible in the table view. Possible values range from 0 to the number indicated by **cCategories**.
    
 **aSort**
  
> Array of **SSortOrder** structures, each defining a sort order. 
    
## Remarks

A **SSortOrderSet** structure is used for defining multiple sort orders for standard and categorized sorting. 
  
Each **SSortOrderSet** structure contains at least one **SSortOrder** structure defining the direction of the sort and the column that will be used as the sort key. For categorized sorting, this column is used as the category. When the value of the **cSorts** member exceeds the value of the **cCategories** member, there are more sort keys than categories, and categories are created from the columns that appear first in the **SSortOrder** array. 
  
For example, if **cSorts** is set to 3 and **cCategories** is set to 2, the columns described by the **ulPropTag** member of the first two entries in the **SSortOrder** array are used as the category columns. The first entry serves as the top-level category grouping; the second entry as the secondary grouping. All of the rows that match the two category columns are sorted by using the sort key defined in the third entry. 
  
The **cExpanded** member specifies the number of categories that are at first expanded. When there are multiple categories, the table implementation starts with the first column to be designated as a category and continues in sequential order with the subsequent category columns until the number of **cCategories** has been exceeded. If there are more category columns than there are expanded columns, the category columns are collapsed. If **cExpanded** is equal to zero, only the top level heading row is available to the table user for display. If **cExpanded** is equal to one less than the number of categories, then all of the heading rows and none of the leaf rows are available. If **cExpanded** is equal to the number of categories, then the table is fully expanded. 
  
For more information about standard and categorized sorting, see [Sorting and Categorization](sorting-and-categorization.md).
  
## See also



[SSortOrder](ssortorder.md)
  
[IMAPITable::ExpandRow](imapitable-expandrow.md)
  
[IMAPITable::CollapseRow](imapitable-collapserow.md)


[MAPI Structures](mapi-structures.md)

