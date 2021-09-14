---
title: "SSortOrder"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SSortOrder
api_type:
- COM
ms.assetid: fe181b9a-5903-4cc0-bcd5-2061b440b5b1
description: "Last modified: March 09, 2015"
---

# SSortOrder
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
Defines how to sort the rows of a table, what column to use as the sort key, and the direction of the sort. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SSortOrder
{
  ULONG ulPropTag;
  ULONG ulOrder;
} SSortOrder, FAR *LPSSortOrder;

```

## Members

**ulPropTag**
  
> Property tag identifying the sort key or, for a categorized sort, the category column.
    
**ulOrder**
  
> The order in which the data is to be sorted. Possible values are as follow:
    
  - TABLE_SORT_ASCEND: The table should be sorted in ascending order.
      
  - TABLE_SORT_COMBINE: The sort operation should create a category that combines the property identified as the sort key column in the **ulPropTag** member with the sort key column specified in the previous **SSortOrder** structure. 
      
    TABLE_SORT_COMBINE can only be used when the **SSortOrder** structure is being used as an entry in an [SSortOrderSet](ssortorderset.md) structure to specify multiple sort orders for a categorized sort. TABLE_SORT_COMBINE cannot be used in the first **SSortOrder** structure in an **SSortOrderSet** structure. 
      
  - TABLE_SORT_DESCEND: The table should be sorted in descending order.
      
  - TABLE_SORT_CATEG_MAX: The table should be sorted on the maximum value of the **ulPropTag** member for the data rows in the categories specified by the previous sort order in the **SSortOrderSet** structure. 
      
  - TABLE_SORT_CATEG_MIN: The table should be sorted on the minimum value of the **ulPropTag** member for the data rows in the categories specified by the previous sort order in the in **SSortOrderSet** structure. 
    
## Remarks

An **SSortOrder** structure is used to describe how to perform either a standard sort operation or a categorized sort operation. **SSortOrder** structures are typically combined into an **SSortOrderSet** structure to describe multiple sort keys and directions. **SSortOrderSet** structures are used in the following functions and interface methods: 
  
- [ITableData::HrGetView](itabledata-hrgetview.md)
    
- [IMAPIFolder::SaveContentsSort](imapifolder-savecontentssort.md)
    
- [IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
    
- [IMAPITable::SortTable](imapitable-sorttable.md)
    
- [FBadSortOrderSet](fbadsortorderset.md)
    
- [HrQueryAllRows](hrqueryallrows.md)
    
The range of allowed columns in a table that can be used as a sort key depends on the provider. Columns that are part of the current column set can always be used as sort keys. However, each provider determines whether sort keys can be defined by using available columns that are not in the current column set. An available column is a column that is returned from [IMAPITable::QueryColumns](imapitable-querycolumns.md) when the TBL_ALL_COLUMNS flag is set. 
  
The **ulOrder** member indicates both directional order and categorization information, for example, by conversation ([PidTagConversationTopic](pidtagconversationtopic-canonical-property.md)), that is, conversational thread, which is a series of messages and replies. Rows can be sorted in either an ascending or descending sequence with all NULL entries positioned last. 
  
The TABLE_SORT_COMBINE value indicates that the column specified in **ulPropTag** should be combined with the previous category column to form a composite category. That is, instead of categorizing on unique values of individual columns, TABLE_SORT_COMBINE allows for categorization on unique values of a combination of columns. For example, a single category could be defined to group messages received from a particular sender on a particular subject. Setting the value to TABLE_SORT_COMBINE reduces the number of category rows that are displayed. 
  
Sorting on multi-valued columns is not universally supported by all table implementations. If supported, apply the MV_FLAG using the MVI_PROP macro to the property tag in the **ulPropTag** member to identify the sort key as a multi-valued column. Sorting on a multi-valued column is based on using the individual values. 
  
> [!IMPORTANT]
> The **ulOrder** member values TABLE_SORT_CATEG_MAX and TABLE_SORT_CATEG_MIN might not be defined in the downloadable header file you currently have, in which case you can add it to your code using the following values: >  `#define TABLE_SORT_CATEG_MAX ((ULONG) 0x00000004)`>  `#define TABLE_SORT_CATEG_MIN ((ULONG) 0x00000008)`
  
For more information about standard and categorized sorting, see [Sorting and Categorization](sorting-and-categorization.md). 
  
## See also

- [SSortOrderSet](ssortorderset.md)
- [MAPI Structures](mapi-structures.md)

