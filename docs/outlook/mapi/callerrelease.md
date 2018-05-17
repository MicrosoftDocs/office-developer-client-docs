---
title: "CALLERRELEASE"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- CALLERRELEASE
api_type:
- HeaderDef
ms.assetid: 80ba893d-3380-4db1-9175-f5b84cb57def
description: "Last modified: March 09, 2015"
---

# CALLERRELEASE

  
  
**Applies to**: Outlook 
  
Defines a callback function that can release a table data object when a table view is being released. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Defined function implemented by:  <br/> |Client applications and service providers  <br/> |
|Defined function called by:  <br/> |MAPI  <br/> |
   
```
void CALLERRELEASE(
  ULONG_PTR ulCallerData,
  LPTABLEDATA lpTblData,
  LPMAPITABLE lpVue
);
```

## Parameters

 _ulCallerData_
  
> [in] Caller data saved by MAPI with the table view and passed to the **CALLERRELEASE** based callback function. The data provides context about the table view being released. 
    
 _lpTblData_
  
> [in] Pointer to the [ITableData : IUnknown](itabledataiunknown.md) interface for the table data object underlying the table view being released. 
    
 _lpVue_
  
> [in] Pointer to the [IMAPITable : IUnknown](imapitableiunknown.md) interface for the table view being released. This is an interface for the table object returned in the  _lppMAPITable_ parameter of the [ITableData::HrGetView](itabledata-hrgetview.md) method that created the object to release. 
    
## Return value

None 
  
## Remarks

A client application or service provider that has populated a table data object can call [ITableData::HrGetView](itabledata-hrgetview.md) to create a read-only, sorted view of the table. The call to **HrGetView** passes a pointer to a **CALLERRELEASE** based callback function and also a context to be saved with the table view. When the reference count of the table view returns to zero and the view is being released, the **IMAPITable** implementation calls the callback function, passing the context in the  _ulCallerData_ parameter. 
  
A common use of a **CALLERRELEASE** based callback function is to release the underlying table data object and not have to keep track of it during subsequent processing. 
  

