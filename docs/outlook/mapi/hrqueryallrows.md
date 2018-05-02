---
title: "HrQueryAllRows"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- HrQueryAllRows
api_type:
- HeaderDef
ms.assetid: b08fadcf-cdf3-48b7-9489-d7f745266482
description: "Last modified: March 09, 2015"
---

# HrQueryAllRows

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Retrieves all rows of a table. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
HRESULT HrQueryAllRows(
  LPMAPITABLE ptable,
  LPSPropTagArray ptaga,
  LPSRestriction pres,
  LPSSortOrderSet psos,
  LONG crowsMax,
  LPSRowSet FAR * pprows
);
```

## Parameters

 _ptable_
  
> [in] Pointer to the MAPI table from which rows are retrieved. 
    
 _ptaga_
  
> [in] Pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags indicating table columns. These tags are used to select the specific columns to be retrieved. If the  _ptaga_ parameter is NULL, **HrQueryAllRows** retrieves the entire column set of the current table view passed in the  _ptable_ parameter. 
    
 _pres_
  
> [in] Pointer to an [SRestriction](srestriction.md) structure that contains retrieval restrictions. If the  _pres_ parameter is NULL, **HrQueryAllRows** makes no restrictions. 
    
 _psos_
  
> [in] Pointer to an [SSortOrderSet](ssortorderset.md) structure identifying the sort order of the columns to be retrieved. If the  _psos_ parameter is NULL, the default sort order for the table is used. 
    
 _crowsMax_
  
> [in] Maximum number of rows to be retrieved. If the value of the  _crowsMax_ parameter is zero, no limit on the number of rows retrieved is set. 
    
 _pprows_
  
> [out] Pointer to a pointer to the returned [SRowSet](srowset.md) structure that contains an array of pointers to the retrieved table rows. 
    
## Return value

S_OK 
  
> The call retrieved the expected rows of a table. 
    
MAPI_E_TABLE_TOO_BIG 
  
> The number of rows in the table is larger than the number passed for the  _crowsMax_ parameter. 
    
## Remarks

A client application or service provider has no control over the number of rows **HrQueryAllRows** attempts to retrieve, other than by imposing a restriction pointed to by the  _pres_ parameter. The  _crowsMax_ parameter does not limit the retrieval to a certain number of table rows, but rather defines a maximum amount of memory available to hold all retrieved rows. The only protection against massive memory overflow is the stopgap feature provided by setting  _crowsMax_. The error return MAPI_E_TABLE_TOO_BIG means the table contains too many rows to be held all at once in memory. 
  
Tables that are typically small, such as a message store table or a provider table, usually can be safely retrieved with **HrQueryAllRows**. Tables at risk of being very large, such as a contents table or even a recipients table, should be traversed in subsections using the [IMAPITable::QueryRows](imapitable-queryrows.md) method. 
  
If any table properties are undefined when **HrQueryAllRows** is called, they are returned with property type PT_NULL and property identifier PROP_ID_NULL 
  

