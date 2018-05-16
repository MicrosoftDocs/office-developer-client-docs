---
title: "Setting Table Position with a Fractional Value"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 80d31611-e508-4b17-b482-bedf76db26ff
description: "Last modified: July 23, 2011"
 
 
---

# Setting Table Position with a Fractional Value

  
  
**Applies to**: Outlook 
  
Table users can move to a position that represents an approximate percentage of rows in relation to the total. Rather than moving to an exact row, this method of positioning divides the table into portions based on fractions. Table users can move, for example, to a table's half-way point or to the row that is 7/8 of the way through the table. 
  
 **To move the cursor an approximate number of rows**
  
- Call [IMAPITable::SeekRowApprox](imapitable-seekrowapprox.md). **SeekRowApprox** moves to the row that represents a particular percentage of rows in relation to the beginning of the table. This percentage is specified in the  _ulNumerator_ and  _ulDenominator_ parameters. **SeekRowApprox** is used frequently to implement scroll bars. 
    
 **To determine a table's approximate position**
  
- Call [IMAPITable::QueryPosition](imapitable-queryposition.md). **QueryPosition** can be used to inform the user of the current position. It sets a fractional value based on the number of rows in the table and the number of the current row. Expect that this value represents an approximation. Table implementers are encouraged not to calculate the exact position because accurate implementations can be expensive to invoke, especially on categorized tables. 
    
## See also

#### Concepts

[MAPI Tables](mapi-tables.md)

