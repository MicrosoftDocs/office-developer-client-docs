---
title: "How to Verify an Attachment is Blocked"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
ms.assetid: 69663470-45f3-86ed-e015-eba32b5a7233
description: "Last modified: June 25, 2012"
 
 
---

# How to: Verify an Attachment is Blocked

  
  
**Applies to**: Outlook 
  
This code sample in C++ shows how to use the [IAttachmentSecurity : IUnknown](iattachmentsecurityiunknown.md) interface to find out whether an attachment is blocked by Microsoft Outlook 2010 or Microsoft Outlook 2013 for viewing and indexing. 
  
[IAttachmentSecurity : IUnknown](iattachmentsecurityiunknown.md) is derived from the [IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28VS.85%29.aspx) interface. You can obtain the [IAttachmentSecurity : IUnknown](iattachmentsecurityiunknown.md) interface by calling [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx) on the MAPI session object, requesting **IID_IAttachmentSecurity**. [IAttachmentSecurity::IsAttachmentBlocked](iattachmentsecurity-isattachmentblocked.md) returns **true** in  _pfBlocked_ if the attachment is considered unsafe by Outlook 2010 or Outlook 2013 and is blocked for viewing and indexing in Outlook 2010 or Outlook 2013. 
  
```
HRESULT IsAttachmentBlocked(LPMAPISESSION lpMAPISession, LPCWSTR pwszFileName, BOOL* pfBlocked) 
{ 
    if (!lpMAPISession || !pwszFileName || !pfBlocked) return MAPI_E_INVALID_PARAMETER; 
 
    HRESULT hRes = S_OK; 
    IAttachmentSecurity* lpAttachSec = NULL; 
    BOOL bBlocked = false; 
 
    hRes = lpMAPISession-&amp;gt;QueryInterface(IID_IAttachmentSecurity,(void**)&amp;amp;lpAttachSec); 
    if (SUCCEEDED(hRes) &amp;amp;&amp;amp; lpAttachSec) 
    { 
        hRes = lpAttachSec-&amp;gt;IsAttachmentBlocked(pwszFileName,&amp;amp;bBlocked); 
    } 
    if (lpAttachSec) lpAttachSec-&amp;gt;Release(); 
 
    *pfBlocked = bBlocked; 
    return hRes; 
}

```


