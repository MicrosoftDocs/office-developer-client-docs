---
title: "HrProcessConvActionForSentItem"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 08121e33-7820-4a31-b6da-06a4a54ec43f
description: "Performs post-send categorization on a mail item based on its PidTagConversationId."
 
 
---

# HrProcessConvActionForSentItem

Performs post-send categorization on a mail item based on its [PidTagConversationId](http://msdn.microsoft.com/library/f8e4a5fa-cb73-4eca-b174-72e1fda821a6%28Office.15%29.aspx).
  
## Quick Info

|||
|:-----|:-----|
|Exported by:  <br/> |Outlook.exe  <br/> |
|Called by:  <br/> |Client  <br/> |
|Implemented by:  <br/> |Outlook  <br/> |
   
```
HRESULT WINAPI HrProcessConvActionForSentItem( 
    SBinary const *pmbinStoreEid, 
    SBinary const *pmbinMsgEid, 
    SBinary const *pmbinConvID, 
    DWORD dwFlags)
```

## Parameters

 _pmbinStoreEid_
  
> [in] The [PidTagEntryId](http://msdn.microsoft.com/library/ca02e873-c2d2-4d58-8df8-c05fbcdc8fba%28Office.15%29.aspx) of the store, or the [PidTagStoreEntryId](http://msdn.microsoft.com/library/0d705667-19f4-4eda-a068-e65ea8f00d9b%28Office.15%29.aspx) of the mail item. Cannot be NULL or invalid. 
    
 _pmbinMsgEid_
  
> [in] The [PidTagEntryId](http://msdn.microsoft.com/library/ca02e873-c2d2-4d58-8df8-c05fbcdc8fba%28Office.15%29.aspx) of the mail item. Cannot be NULL or invalid. 
    
 _pmbinConvID_
  
> [in] The [PidTagConversationId](http://msdn.microsoft.com/library/f8e4a5fa-cb73-4eca-b174-72e1fda821a6%28Office.15%29.aspx) of the mail item. Cannot be NULL or invalid. 
    
 _dwFlags_
  
> [in] A bitmask that specifies additional information about the method call.
    
    - 0—No additional options are used in this method call. This is the recommended value. 
    
    - **PCAFSIF_MSGEID_IS_SEARCH_KEY**— _pmbinMsgEid_ is actually the [PidTagSearchKey](http://msdn.microsoft.com/library/fcab369a-a1f4-4425-a272-e35046914a4d%28Office.15%29.aspx) of the message. Using a **PidTagSearchKey** is resource intensive, and should be avoided if a [PidTagEntryId](http://msdn.microsoft.com/library/ca02e873-c2d2-4d58-8df8-c05fbcdc8fba%28Office.15%29.aspx) is available. 
    
## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |The call was successful.  <br/> |
|E_INVALIDARG  <br/> | _dwFlags_ contains an unknown flag.  <br/> |
   
## Remarks

Categories are considered personal information and should not be transmitted outside the mailbox of the user. Therefore, do not call **HrProcessConvActionForSentItem** on an unsent mail item. Instead, send the item, and then call **HrProcessConvActionForSentItem** on the archived copy. The archived copy may be stored in the Sent Items folder, or an equivalent location. 
  
Your application must be in-process with Outlook.exe, such as from a COM add-in, to call **HrProcessConvActionForSentItem**. If you attempt to call **HrProcessConvActionForSentItem** out-of-process, **HrProcessConvActionForSentItem** will throw an access-violation exception. 
  

