---
title: "IMAPISupportSpoolerYield"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.SpoolerYield
api_type:
- COM
ms.assetid: f5c6ba8f-4ef5-4d60-b4e6-5b9160ec4e99
description: "Last modified: July 23, 2011"
---

# IMAPISupport::SpoolerYield

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Gives control of the CPU to the MAPI spooler so that it can perform any tasks it considers necessary.
  
```cpp
HRESULT SpoolerYield(
ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> Reserved; must be zero.
    
## Return value

S_OK 
  
> The transport provider successfully released the CPU.
    
MAPI_W_CANCEL_MESSAGE 
  
> Instructs the transport provider to stop the delivery of the message to any recipients that have not yet received it.
    
## Remarks

The **IMAPISupport::SpoolerYield** method is implemented for transport provider support objects. Transport providers call **SpoolerYield** to allow the MAPI spooler to accomplish any necessary processing. 
  
## Notes to callers

Call **SpoolerYield** when you are performing lengthy operations that can be paused. This allows foreground applications to run during a long operation, such as delivery to a large recipient list across a busy network. 
  
If **SpoolerYield** returns with MAPI_W_CANCEL_MESSAGE, the MAPI spooler has determined that the message should no longer be sent. Return MAPI_E_USER_CANCEL to your calling process and exit, if possible. 
  
For more information about yielding to the MAPI spooler, see [Interacting with the MAPI Spooler](interacting-with-the-mapi-spooler.md).
  
## See also



[IMAPISupport : IUnknown](imapisupportiunknown.md)

