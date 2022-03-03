---
title: "Sorting Tables After Setting Columns and Restrictions"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 57db0314-1df0-4fd2-b443-223b0512f1ad
 
 
---

# Sorting Tables After Setting Columns and Restrictions

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
When you need to limit the view of a sorted table, always make the following **IMAPITable** calls in the following order: 
  
1. [IMAPITable::SetColumns](imapitable-setcolumns.md) to define the column set. 
    
2. [IMAPITable::Restrict](imapitable-restrict.md) to impose the restriction. 
    
3. [IMAPITable::SortTable](imapitable-sorttable.md) to perform the sort. 
    
If the sorted table is categorized, make a call to [IMAPITable::SetCollapseState](imapitable-setcollapsestate.md), if necessary, after the **SortTable** call. This ordering of calls is important because most service providers sort a table as the last task to achieve the best performance. If, for example, a message store provider must categorize a folder contents table before a restriction can be imposed, this categorization will be removed during the processing of the restriction. A second categorization will be necessary. 
  

