---
title: "IMsgServiceAdminGetProviderTable"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin.GetProviderTable
api_type:
- COM
ms.assetid: 7180bff2-91ad-4e11-923e-2a9acefa3215
---

# IMsgServiceAdmin::GetProviderTable

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides access to the provider table, a listing of the service providers in the profile.
  
```cpp
HRESULT GetProviderTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] Always NULL.
    
 _lppTable_
  
> [out] A pointer to a pointer to the provider table.
    
## Return value

S_OK 
  
> The provider table was successfully returned.
    
## Remarks

The **IMsgServiceAdmin::GetProviderTable** method provides access to the MAPI provider table, a table that lists all the address book, message store, and transport providers currently installed in the profile. 
  
Unlike the provider table returned through the [IProviderAdmin::GetProviderTable](iprovideradmin-getprovidertable.md) method, the provider table returned through **IMsgServiceAdmin::GetProviderTable** cannot include additional rows that represent information associated with one or more service providers in the profile. 
  
Providers that have been deleted, or are in use but have been marked for deletion, are not included in the provider table. Provider tables are static, meaning that subsequent additions to or deletions from the profile are not reflected in the table. 
  
If the profile has no providers, **GetProviderTable** returns a table with zero rows and the S_OK return value. 
  
For a complete list of the columns in the provider table, see [Provider Table](provider-tables.md). 
  
## Notes to callers

To retrieve the rows of a provider table in transport order, use the following procedure:
  
1. Call the [IMAPITable::Restrict](imapitable-restrict.md) method to impose a property restriction that matches the **PR_RESOURCE_TYPE** ([PidTagResourceType](pidtagresourcetype-canonical-property.md)) property with MAPI_TRANSPORT_PROVIDER.
    
2. Call the [IMAPITable::SortTable](imapitable-sorttable.md) method to sort the table by the **PR_PROVIDER_ORDINAL** ([PidTagProviderOrdinal](pidtagproviderordinal-canonical-property.md)) column. 
    
3. Call the [IMAPITable::QueryRows](imapitable-queryrows.md) method to get the rows of the table. 
    
An alternative to these calls is to make a single call to the [HrQueryAllRows](hrqueryallrows.md) function with all of the appropriate data structures passed in. 
  
If you retrieve the **PR_SERVICE_UID** ([PidTagServiceUid](pidtagserviceuid-canonical-property.md)) columns in each of the rows, you can use this array of **MAPIUID** structures to set the transport order in a call to [IMsgServiceAdmin::MsgServiceTransportOrder](imsgserviceadmin-msgservicetransportorder.md).
  
Setting the MAPI_UNICODE flag in the _ulFlags_ parameter does the following: 
  
- Sets the string type to Unicode for data returned for the initial active columns of the provider table by the [IMAPITable::QueryColumns](imapitable-querycolumns.md) method. The initial active columns for a provider table are those columns the **QueryColumns** method returns before the provider that contains the table calls the [IMAPITable::SetColumns](imapitable-setcolumns.md) method. 
    
- Sets the string type to Unicode for data returned for the initial active rows of the provider table by **QueryRows**. The initial active rows for a provider table are those rows **QueryRows** returns before the provider that contains the table calls **SetColumns**. 
    
- Controls the property types of the sort order returned by the [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) method before the client that contains the provider table calls the [IMAPITable::SortTable](imapitable-sorttable.md) method. 
    
## See also



[IMsgServiceAdmin::GetMsgServiceTable](imsgserviceadmin-getmsgservicetable.md)
  
[IMsgServiceAdmin::MsgServiceTransportOrder](imsgserviceadmin-msgservicetransportorder.md)
  
[IProviderAdmin::GetProviderTable](iprovideradmin-getprovidertable.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)

