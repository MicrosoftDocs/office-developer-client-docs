---
title: "CreateTable"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- CreateTable
api_type:
- HeaderDef
ms.assetid: 106ce3d8-d0bf-4a0e-9a15-dc8988d0eb58
description: "Last modified: March 09, 2015"
---

# CreateTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Creates structures and an object handle for an [ITableData](itabledataiunknown.md) object which can be used to create table contents. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE CreateTable(
  LPCIID lpInterface,
  ALLOCATEBUFFER FAR * lpAllocateBuffer,
  ALLOCATEMORE FAR * lpAllocateMore,
  FREEBUFFER FAR * lpFreeBuffer,
  LPVOID lpvReserved,
  ULONG ulTableType,
  ULONG ulPropTagIndexColumn,
  LPSPropTagArray lpSPropTagArrayColumns,
  LPTABLEDATA FAR * lppTableData
);
```

## Parameters

 _lpInterface_
  
> [in] Pointer to an interface identifier (IID) for the table data object. The valid interface identifier is IID_IMAPITableData. Passing NULL in the  _lpInterface_ parameter also causes the table data object returned in the  _lppTableData_ parameter to be cast to the standard interface for a table data object. 
    
 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory. 
    
 _lpAllocateMore_
  
> [in] Pointer to the [MAPIAllocateMore](mapiallocatemore.md) function, to be used to allocate additional memory. 
    
 _lpFreeBuffer_
  
> [in] Pointer to the [MAPIFreeBuffer](mapifreebuffer.md) function, to be used to free memory. 
    
 _lpvReserved_
  
> [in] Reserved; must be zero. 
    
 _ulTableType_
  
> [in] A table type that is available to a client application or service provider as part of the [IMAPITable::GetStatus](imapitable-getstatus.md) return data on its table views. Possible values are: 
    
TBLTYPE_DYNAMIC 
  
> The table's contents are dynamic and can change as the underlying data changes. 
    
TBLTYPE_KEYSET 
  
> The rows in the table are fixed, but the values in these rows are dynamic and can change as the underlying data changes. 
    
TBLTYPE_SNAPSHOT 
  
> The table is static and the contents do not change when the underlying data changes. 
    
 _ulPropTagIndexColumn_
  
> [in] Index number of the column for use when changing table data. 
    
 _lpSPropTagArrayColumns_
  
> [in] Pointer to an [SPropTagArray](sproptagarray.md) structure that contains an array of property tags indicating the properties required in the table for which the object holds data. 
    
 _lppTableData_
  
> [out] Pointer to a pointer to the returned table data object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

The  _lpAllocateBuffer_,  _lpAllocateMore_, and  _lpFreeBuffer_ input parameters point to the [MAPIAllocateBuffer](mapiallocatebuffer.md), [MAPIAllocateMore](mapiallocatemore.md), and [MAPIFreeBuffer](mapifreebuffer.md) functions, respectively. A client application calling **CreateTable** passes in pointers to the MAPI functions just named; a service provider passes the pointers to these functions that it received in its initialization call or retrieved with a call to the [IMAPISupport::GetMemAllocRoutines](imapisupport-getmemallocroutines.md) method. 
  
## See also



[IMAPITable : IUnknown](imapitableiunknown.md)

