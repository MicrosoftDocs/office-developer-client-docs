---
title: "IMsgServiceAdminMsgServiceTransportOrder"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin.MsgServiceTransportOrder
api_type:
- COM
ms.assetid: c57ada0e-b9a1-496b-8548-75686d8cba4e
description: "Last modified: July 23, 2011"
---

# IMsgServiceAdmin::MsgServiceTransportOrder

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the order in which transport providers are called to deliver a message.
  
```cpp
HRESULT MsgServiceTransportOrder(
  ULONG cUID,
  LPMAPIUID lpUIDList,
  ULONG ulFlags    
);
```

## Parameters

 _cUID_
  
> [in] The count of unique identifiers in the _lpUIDList_ parameter. 
    
 _lpUIDList_
  
> [in] A pointer to an array of unique identifiers that represent transport providers. The array contains one identifier for each transport provider configured in the current profile.
    
 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The transport order was set successfully.
    
MAPI_E_BUSY 
  
> The value in the _cUID_ parameter differs from the number of transport providers actually in the profile. 
    
MAPI_E_NOT_FOUND 
  
> One or more of the [MAPIUID](mapiuid.md) structures passed in the _lpUIDList_ parameter do not refer to a transport provider currently in the profile. 
    
## Remarks

The **IMsgServiceAdmin::MsgServiceTransportOrder** method sets the delivery order of transport providers in a profile. The  _lpUIDList_ parameter must contain a sorted list of transport-provider entry identifiers obtained from the **PR_PROVIDER_UID** ([PidTagProviderUid](pidtagprovideruid-canonical-property.md)) property of the table returned from the [IMsgServiceAdmin::GetProviderTable](imsgserviceadmin-getprovidertable.md) method. A client application must pass the complete list in  _lpUIDList_.
  
 **SetTransportOrder** overrides transport provider preferences such as the STATUS_XP_PREFER_LAST flag set in the **PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) property. 
  
## See also



[MAPIUID](mapiuid.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)

