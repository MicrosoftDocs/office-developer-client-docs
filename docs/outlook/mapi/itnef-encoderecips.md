---
title: "ITnefEncodeRecips"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITnef.EncodeRecips
api_type:
- COM
ms.assetid: b3ce4b0e-4f48-4a7e-a30c-c4754bccb12c
description: "Last modified: July 23, 2011"
---

# ITnef::EncodeRecips

  
  
**Applies to**: Outlook 
  
Encodes a view for a message's recipient table in the Transport-Neutral Encapsulation Format (TNEF) data stream for the message.
  
```
HRESULT EncodeRecips(
  ULONG ulFlags,
  LPMAPITABLE lpRecipientTable
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpRecipientTable_
  
> [in] A pointer to the recipient table for which the view is encoded. The  _lpRecipientTable_ parameter can be NULL. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

Transport providers, message store providers, and gateways call the **ITnef::EncodeRecips** method to perform TNEF encoding for a particular recipient table view. TNEF encoding is useful, for example, if a provider or gateway requires a particular column set, sort order, or restriction for the recipient table. 
  
A provider or gateway passes the table view to be encoded in the  _lpRecipientTable_ parameter. The TNEF implementation encodes the recipient table with the given view, using the given column set, sort order, restriction, and position. If a provider or gateway passes NULL in  _lpRecipientTable_, TNEF gets the recipient table from the message being encoded by using the [IMessage::GetRecipientTable](imessage-getrecipienttable.md) method, and processes every row of the table into the TNEF stream by using the table's current settings. 
  
Calling **EncodeRecips** with NULL in  _lpRecipientTable_ thus encodes all message recipients and is equivalent to calling the [ITnef::AddProps](itnef-addprops.md) method with the TNEF_PROP_INCLUDE flag in its  _ulFlags_ parameter and the **PR_MESSAGE_RECIPIENTS** ([PidTagMessageRecipients](pidtagmessagerecipients-canonical-property.md)) property in its  _lpPropList_ parameter. 
  
Note that it is rarely necessary to call **EncodeRecips** unless there is a requirement to encode a particular recipient table view. Foreign messaging systems almost always have facilities for handling recipient lists that are powerful enough to handle the common needs of encoding recipient lists; therefore, these systems almost never require TNEF for this purpose. 
  
## See also

#### Reference

[IMessage::GetRecipientTable](imessage-getrecipienttable.md)
  
[ITnef::AddProps](itnef-addprops.md)
  
[PidTagMessageRecipients Canonical Property](pidtagmessagerecipients-canonical-property.md)
  
[ITnef : IUnknown](itnefiunknown.md)

