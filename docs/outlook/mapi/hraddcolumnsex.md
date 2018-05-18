---
title: "HrAddColumnsEx"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.HrAddColumnsEx
api_type:
- COM
ms.assetid: c0a65d2b-a9b8-4477-a1c7-18c8478126f6
description: "Last modified: March 09, 2015"
---

# HrAddColumnsEx

  
  
**Applies to**: Outlook 
  
Adds or moves columns to the beginning of an existing table. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
HRESULT HrAddColumnsEx(
  LPMAPITABLE lptbl,
  LPSPropTagArray lpproptagColumnsNew,
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPFREEBUFFER lpFreeBuffer,
  void (FAR * lpfnFilterColumns)(
  LPSPropTagArray ptaga)
);
```

## Parameters

 _lptbl_
  
> [in] Pointer to the MAPI table affected. 
    
 _lpproptagColumnsNew_
  
> [in] Pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags for the properties to be added or moved to the beginning of the table. 
    
 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory. 
    
 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory. 
    
 _lpfnFilterColumns_
  
> [in] Pointer to a callback function furnished by the caller. If the  _lpfnFilterColumns_ parameter is set to NULL, no callback is made. 
    
 _ptaga_
  
> [in] Pointer to an [SPropTagArray](sproptagarray.md) structure that contains the array of property tags already existing in the table before properties are added or moved to the beginning. **HrAddColumnsEx** passes this pointer as the parameter to the callback function pointed to by  _lpfnFilterColumns_.
    
## Return value

S_OK 
  
> The call succeeded and the specified columns were moved or added.
    
## Remarks

The properties passed to **HrAddColumnsEx** using the  _lpproptagColumnsNew_ parameter become the first properties exposed on subsequent calls to the [IMAPITable::QueryRows](imapitable-queryrows.md) method. Any properties previously in the table that were not specified in the  _lpproptagColumnsNew_ parameter are exposed after all the added and moved properties. 
  
If any table properties are undefined when **QueryRows** is called, they are returned with property type PT_NULL and property identifier PROP_ID_NULL. 
  
## Notes to callers

The **HrAddColumnsEx** function allows the caller to furnish a callback function to filter the columns that were already in the table, for example to convert strings from property type PT_UNICODE to PT_STRING8. **HrAddColumnsEx** passes a pointer to the previously existing column set as the parameter to the callback function. The callback function can change data in the property tag array but cannot add new tags. 
  
 **HrAddColumnsEx** first calls the callback function if one is furnished, then adds or moves the specified columns, and finally calls [IMAPITable::SetColumns](imapitable-setcolumns.md). 
  
The  _lpAllocateBuffer_ and  _lpFreeBuffer_ input parameters point to the [MAPIAllocateBuffer](mapiallocatebuffer.md) and [MAPIFreeBuffer](mapifreebuffer.md) functions, respectively. The exact values of the pointers passed to **HrAddColumnsEx** depend on whether the caller is a client application or a service provider. A client passes pointers to the MAPI functions with the specified names. A service provider passes the pointers it received in its initialization call or retrieved by calling the [IMAPISupport::GetMemAllocRoutines](imapisupport-getmemallocroutines.md) method. 
  
## See also



[IMAPITable::QueryColumns](imapitable-querycolumns.md)

