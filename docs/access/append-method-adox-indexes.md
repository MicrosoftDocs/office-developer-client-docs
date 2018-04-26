---
title: "Append Method (ADOX Indexes)"
  
  
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 015ebab4-5e9d-8777-ac82-4d20e957c274
---

# Append Method (ADOX Indexes)

Adds a new [Index](index-object-adox.md) object to the [Indexes](indexes-collection-adox.md) collection. 
  
## Syntax

 *Indexes*  . **Append** *Index*  [,  *Columns*  ] 
  
## Parameters

-  *Index* 
    
- The **Index** object to append or the name of the index to create and append. 
    
-  *Columns* 
    
- Optional. A **Variant** value that specifies the name(s) of the column(s) to be indexed. The  *Columns*  parameter corresponds to the value(s) of the [Name](name-property-adox.md) property of a [Column](column-object-adox.md) object or objects. 
    
## Remarks

The  *Columns*  parameter can take either the name of a column or an array of column names. 
  
An error will occur if the provider does not support creating indexes.
  

