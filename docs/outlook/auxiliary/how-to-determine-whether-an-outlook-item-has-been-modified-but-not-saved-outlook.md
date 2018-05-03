---
title: "How to Determine whether an Outlook item has been modified but not saved (Outlook Auxiliary Reference)"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: overview
 
localization_priority: Normal
ms.assetid: 65fba557-5fb0-42de-8715-eccda1f3c648
description: "This topic shows how to use the dispidFDirty dispatch ID to invoke the corresponding property on an Outlook item, to see whether the item has been modified and has not been saved."
---

# How to: Determine whether an Outlook item has been modified but not saved (Outlook Auxiliary Reference)

This topic shows how to use the **dispidFDirty** dispatch ID to invoke the corresponding property on an Outlook item, to see whether the item has been modified and has not been saved. 
  
Given an item object, you can use the [IUnknown::QueryInterface](http://msdn.microsoft.com/library/com.iunknown_queryinterface.aspx) method to obtain an [IDispatch](http://msdn.microsoft.com/library/ebbff4bc-36b2-4861-9efa-ffa45e013eb5%28Office.15%29.aspx) interface pointer. The function in this topic,  `FIsItemDirty`, accepts an **IDispatch** pointer,  _pdisp_, as an input parameter.  `FIsItemDirty` calls the [IDispatch::Invoke](http://msdn.microsoft.com/library/964ade8e-9d8a-4d32-bd47-aa678912a54d%28Office.15%29.aspx) method, specifying **dispidFDirty** as the argument for the  _dispIdMember_ parameter, and the flags  `DISPATCH_METHOD | DISPATCH_PROPERTYGET` for  _wFlags_, to verify whether the item has been modified.  `FIsItemDirty` returns a Boolean value ( **True** to indicate that the item has unsaved changes; otherwise, **False**).
  
```
bool FIsItemDirty(IDispatch *pdisp)
{
    DISPPARAMS dispparams;
    UINT uArgErr;
    HRESULT hr = S_OK;
    CComVariant varDirty;
    dispparams.rgvarg = 0;
    dispparams.cArgs = 0;
    dispparams.cNamedArgs = 0;
    dispparams.rgdispidNamedArgs = NULL;
    hr = pdisp->Invoke(dispidFDirty,
        IID_NULL,
        LOCALE_SYSTEM_DEFAULT,
        DISPATCH_METHOD | DISPATCH_PROPERTYGET,
        &amp;dispparams,
        &amp;varDirty,
        NULL,
        &amp;uArgErr);
    return SUCCEEDED(hr) &amp;&amp; varDirty.bVal;
}

```

## See also

#### Concepts

[Constants (Outlook exported APIs)](constants-outlook-exported-apis.md)

