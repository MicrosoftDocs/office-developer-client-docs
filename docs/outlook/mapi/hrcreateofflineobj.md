---
title: "HrCreateOfflineObj"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 04d57c1d-ce91-42ce-9f0f-00563092f6f4
description: "Last modified: March 09, 2015"
---

# HrCreateOfflineObj

  
  
**Applies to**: Outlook 
  
 Creates a MAPI offline object that is used by the provider and store in order to notify MAPI when the object goes online and offline, 
  
|||
|:-----|:-----|
|Exported by:  <br/> |Msmapi32.dll  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
|Called by:  <br/> |Client  <br/> |
   
```
STDAPI HrCreateOfflineObj(
ULONG ulFlags,
MAPIOFFLINE_CREATEINFO* pCreateInfo,
IMAPIOfflineMgr** ppOffline
);
```

## Parameters

 _ulFlags_
  
> [in] It must be 0.
    
 _pCreateInfo_
  
> [in] A pointer to a **MAPIOFFLINE_CREATEINFO** structure that contains the information needed to create the offline object. 
    
 _ppOffline_
  
> [out] A pointer to the **IMAPIOfflineMgr** interface. 
    
## Return value

None.
  
HrOpenOfflineObj
  
## Example

```
// create/get global offline object to use as parent.
 ZeroMemory(&amp;OfflineCreateInfo, sizeof(OfflineCreateInfo));
  OfflineCreateInfo.ulSize = sizeof(OfflineCreateInfo);
  OfflineCreateInfo.ulCreateFlags = 0;
  OfflineCreateInfo.pwszProfileName = pszProfileName;
  OfflineCreateInfo.ulCapabilities = ulCapabilities;
  OfflineCreateInfo.pGUID = &amp;GUID_GlobalState;
  OfflineCreateInfo.pInstance = NULL;
  OfflineCreateInfo.pParent = NULL;
  OfflineCreateInfo.pMAPISupport = NULL;
  OfflineCreateInfo.pAggregateInfo = NULL;
  OfflineCreateInfo.pConnectInfo = NULL;
// Create an offline object for the provider with global as parent.
  ZeroMemory(&amp;OfflineCreateInfo, sizeof(OfflineCreateInfo));
  OfflineCreateInfo.ulSize = sizeof(OfflineCreateInfo);
  OfflineCreateInfo.ulCreateFlags = 0;
  OfflineCreateInfo.pwszProfileName = pszProfileName;
  OfflineCreateInfo.ulCapabilities = ulCapabilities;
  OfflineCreateInfo.pGUID = pGuid;
  OfflineCreateInfo.pInstance = pInstance;
  OfflineCreateInfo.pParent = pGlobalOfflineMgr;
  OfflineCreateInfo.pMAPISupport = NULL;
  OfflineCreateInfo.pAggregateInfo = NULL;
  OfflineCreateInfo.pConnectInfo = NULL;
  // create store offline object which aggregates with the store object and has provider offline object as parent.
  ZeroMemory(&amp;OfflineCreateInfo, sizeof(OfflineCreateInfo));
  OfflineCreateInfo.ulSize = sizeof(OfflineCreateInfo);
  OfflineCreateInfo.ulCreateFlags = 0;
  OfflineCreateInfo.pwszProfileName = pszProfileName;
  OfflineCreateInfo.ulCapabilities = ulCapabilities;
  OfflineCreateInfo.pGUID = NULL;
  OfflineCreateInfo.pInstance = NULL;
  OfflineCreateInfo.pParent = m_pProviderOfflineMgr;
  OfflineCreateInfo.pMAPISupport = pMAPISup;
  OfflineCreateInfo.pAggregateInfo = &amp;AggregateInfo;
  OfflineCreateInfo.pConnectInfo = NULL;
  ZeroMemory(&amp;AggregateInfo, sizeof(AggregateInfo));
  AggregateInfo.ulSize = sizeof(AggregateInfo);
  AggregateInfo.pOuterObj = (IMsgStore *)this;
  AggregateInfo.pRefTrackRoot = NULL;

```

## See also

#### Reference

[MAPIOFFLINE_AGGREGATEINFO](mapioffline_aggregateinfo.md)
  
[MAPIOFFLINE_CREATEINFO](mapioffline_createinfo.md)

