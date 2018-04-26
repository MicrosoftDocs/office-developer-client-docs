---
title: "AllowNullsEnum"
  
  
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
  
localization_priority: Normal
ms.assetid: 7bb42b38-6b3b-5930-b1d7-16323a3bdf37
---

# AllowNullsEnum

Specifies whether records with null values are indexed.
  
|**Constant**|**Value**|**Description**|
|:-----|:-----|:-----|
|**adIndexNullsAllow** <br/> |0  <br/> |The index does allow entries in which the key columns are null. If a null value is entered in a key column, the entry is inserted into the index.  <br/> |
|**adIndexNullsDisallow** <br/> |1  <br/> |Default. The index does not allow entries in which the key columns are null. If a null value is entered in a key column, an error will occur.  <br/> |
|**adIndexNullsIgnore** <br/> |2  <br/> |The index does not insert entries containing null keys. If a null value is entered in a key column, the entry is ignored and no error occurs.  <br/> |
|**adIndexNullsIgnoreAny** <br/> |4  <br/> |The index does not insert entries where some key column has a null value. For an index having a multi-column key, if a null value is entered in some column, the entry is ignored and no error occurs.  <br/> |
   

