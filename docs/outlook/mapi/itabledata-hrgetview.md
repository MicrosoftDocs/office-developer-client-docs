---
title: "ITableDataHrGetView"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITableData.HrGetView
api_type:
- COM
ms.assetid: 0e2a47be-497b-4031-87ce-60b2635e25f7
description: "Last modified: July 23, 2011"
---

# ITableData::HrGetView

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Creates a table view, returning a pointer to an [IMAPITable](imapitableiunknown.md) implementation. 
  
```
HRESULT HrGetView(
  LPSSortOrderSet lpSSortOrderSet,
  CALLERRELEASE FAR * lpfCallerRelease,
  ULONG_PTR ulCallerData,
  LPMAPITABLE FAR * lppMAPITable
);
```

## Parameters

 _lpSSortOrderSet_
  
> [in] A pointer to a sort order structure that describes the sort order for the table view. If NULL is passed in the  _lpSSortOrderSet_ parameter, the view is not sorted. 
    
 _lpfCallerRelease_
  
> [in] A pointer to a callback function based on the [CALLERRELEASE](callerrelease.md) prototype that MAPI calls when it releases the view. If NULL is passed in the  _lpfCallerRelease_ parameter, no function is called on release of the view. 
    
 _ulCallerData_
  
> [in] The data that must be saved with the new view and passed to the callback function pointed to by  _lpfCallerRelease_.
    
 _lppMAPITable_
  
> [out] A pointer to a pointer to the newly created view.
    
## Return value

S_OK 
  
> The view was successfully created.
    
## Remarks

The **ITableData::HrGetView** method creates a read-only view of the data in the table, sorted in the order pointed to by the  _lpSSortOrderSet_ parameter. The cursor is placed at the beginning of the first row in the view. An **IMAPITable** interface implementation for accessing the view is returned. 
  
Service providers call **HrGetView** when they need to give a client access to a table. **HrGetView** creates the view and returns the **IMAPITable** pointer. Service providers in turn pass the pointer on to the client. When the client is finished using the table and calls its [IUnknown::Release](http://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) method, **HrGetView** calls the callback function pointed to by the  _lpfCallerRelease_ parameter. 
  
If a service provider needs to return to a client a view that has a customized column set or a restriction, the provider can call the view's [IMAPITable::SetColumns](imapitable-setcolumns.md) and [IMAPITable::Restrict](imapitable-restrict.md) methods before allowing the client access. 
  
## See also

#### Reference

[CALLERRELEASE](callerrelease.md)
  
[IMAPITable : IUnknown](imapitableiunknown.md)
  
[SSortOrderSet](ssortorderset.md)
  
[ITableData : IUnknown](itabledataiunknown.md)

