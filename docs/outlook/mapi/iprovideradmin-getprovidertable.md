---
title: "IProviderAdminGetProviderTable"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProviderAdmin.GetProviderTable
api_type:
- COM
ms.assetid: e9deaa7c-430b-4e97-8ed6-f7c615956e0f
description: "Last modified: March 09, 2015"
---

# IProviderAdmin::GetProviderTable

  
  
**Applies to**: Outlook 
  
Provides access to the message service's provider table, a list of the service providers in the message service.
  
```
HRESULT GetProviderTable(
  ULONG ulFlags,
  LPMAPITABLE FAR * lppTable
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the strings returned in the provider table's columns. The following flag can be set:
    
MAPI_UNICODE 
  
> The string columns are in Unicode format. If the MAPI_UNICODE flag is not set, the columns are in ANSI format.
    
 _lppTable_
  
> [out] A pointer to a pointer to the provider table.
    
## Return value

S_OK 
  
> The provider table was successfully returned.
    
## Remarks

The **IProviderAdmin::GetProviderTable** method retrieves a pointer to the message service's provider table, a table that MAPI maintains that contains information about each service provider in the message service. 
  
Unlike the provider table returned by the [IMsgServiceAdmin::GetProviderTable](imsgserviceadmin-getprovidertable.md) method, the provider table returned by **IProviderAdmin::GetProviderTable** may include additional rows that represent information associated with one or more of the service providers in the message service. This extra information is added to the profile with the "Sections" keyword of the Mapisvc.inf file. When a provider has extra profile sections, it stores the **MAPIUID** structures for these sections in the **PR_SERVICE_EXTRA_UIDS** ( [PidTagServiceExtraUids](pidtagserviceextrauids-canonical-property.md)) property. **PR_SERVICE_EXTRA_UIDS** is saved in the message service profile section. 
  
Providers that have been deleted, or are in use but have been marked for deletion, are not included in the provider table. Provider tables are static, meaning that subsequent additions to or deletions from the message service are not reflected in the table. 
  
If the message service has no providers, **IProviderAdmin::GetProviderTable** returns a table with zero rows and the S_OK return value. 
  
Setting the MAPI_UNICODE flag in the  _ulFlags_ parameter affects the format of the columns returned from the [IMAPITable::QueryColumns](imapitable-querycolumns.md) and [IMAPITable::QueryRows](imapitable-queryrows.md) methods. 
  
This flag also controls the property types in the sort order returned by the [IMAPITable::QuerySortOrder](imapitable-querysortorder.md) method. 
  
For a complete list of the columns in the provider table, see [Provider Table](provider-tables.md). 
  
## Notes to Callers

To retrieve the rows of a provider table in transport order, sort the table by the **PR_PROVIDER_ORDINAL** ( [PidTagProviderOrdinal](pidtagproviderordinal-canonical-property.md)) column. 
  
To retrieve only those rows that represent service providers (without including any extra rows), limit your retrieval to the rows that have a value of PT_ERROR in their **PR_RESOURCE_TYPE** ( [PidTagResourceType](pidtagresourcetype-canonical-property.md)) column.
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
| MsgServiceTableDlg.cpp  <br/> |CMsgServiceTableDlg::OnDisplayItem  <br/> |MFCMAPI uses the **IProviderAdmin::GetProviderTable** method to get the table of providers to render in a new dialog box.  <br/> |
   
## See also

#### Reference

[IMAPITable::QueryColumns](imapitable-querycolumns.md)
  
[IMAPITable::QueryRows](imapitable-queryrows.md)
  
[IMAPITable::QuerySortOrder](imapitable-querysortorder.md)
  
[IMAPITable::SetColumns](imapitable-setcolumns.md)
  
[IMsgServiceAdmin::GetProviderTable](imsgserviceadmin-getprovidertable.md)
  
[IProviderAdmin : IUnknown](iprovideradminiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

