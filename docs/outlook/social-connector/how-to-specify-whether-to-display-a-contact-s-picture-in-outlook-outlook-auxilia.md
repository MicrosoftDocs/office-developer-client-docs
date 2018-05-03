---
title: "How to Specify whether to display a contact's picture in Outlook (Outlook Auxiliary Reference)"
ms.author: null
author: null
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8a454399-0b5c-488a-9b87-5a21a2f0dace
description: "This topic shows how to use the dispidShowSenderPhoto dispatch ID to invoke the corresponding method on an Outlook Explorer or Inspector object, to specify whether to display a contact's picture in the explorer or inspector window, according to a Boolean argument. Specifying VARIANT_TRUE as the argument turns on the display, and VARIANT_FALSE turns off the display."
---

# How to: Specify whether to display a contact's picture in Outlook (Outlook Auxiliary Reference)

This topic shows how to use the **dispidShowSenderPhoto** dispatch ID to invoke the corresponding method on an Outlook [Explorer](http://msdn.microsoft.com/library/026591e5-049f-503a-4166-34e6dbc225fb%28Office.15%29.aspx) or [Inspector](http://msdn.microsoft.com/library/d7384756-669c-0549-1032-c3b864187994%28Office.15%29.aspx) object, to specify whether to display a contact's picture in the explorer or inspector window, according to a Boolean argument. Specifying **VARIANT_TRUE** as the argument turns on the display, and **VARIANT_FALSE** turns off the display. 
  
Given a pointer to an **Explorer** or **Inspector** object, you can use the **IUnknown::QueryInterface** method to obtain an [IDispatch](http://msdn.microsoft.com/library/ebbff4bc-36b2-4861-9efa-ffa45e013eb5%28Office.15%29.aspx) interface pointer. The function in this topic,  `SetSenderContactPhoto`, accepts two input parameters: 
  
-  _inspector_—An **_InspectorPtr** value. 
    
-  _showSenderContactPhoto_—A Boolean value that specifies whether to display contacts' pictures.
    
 `SetSenderContactPhoto` calls the [IDispatch::Invoke](http://msdn.microsoft.com/library/964ade8e-9d8a-4d32-bd47-aa678912a54d%28Office.15%29.aspx) method—specifying **dispidShowSenderPhoto** as the argument for the  _dispIdMember_ parameter, and using  _showSenderContactPhoto_ to form the argument for the  _pDispParams_ parameter—to turn on or off the display according to the value of  _showSenderContactPhoto_.
  
```
void SetSenderContactPhoto(_InspectorPtr inspector, bool showSenderContactPhoto)
{ 
    CComVariant cv;
    IDispatchPtr spdisp;
    DISPPARAMS dispparams;
    EXCEPINFO excepinfo = {0};
    spdisp = inspector;
    cv = showSenderContactPhoto ? VARIANT_TRUE : VARIANT_FALSE;
    dispparams.rgvarg = &amp;cv;
    dispparams.cArgs = 1;
    dispparams.rgdispidNamedArgs = NULL;
    dispparams.cNamedArgs = 0;
    spdisp->Invoke(dispidShowSenderPhoto,
        IID_NULL,
        0,
        DISPATCH_METHOD,
        &amp;dispparams,
        NULL,
        &amp;excepinfo,
        NULL);
}
```

This setting does not persist across Outlook sessions and does not carry from one inspector or explorer to another. The default setting is to turn on the display. This means that if a picture is present, it is displayed. However, if no picture is present, no placeholder picture is displayed.
  
This setting works in conjunction with the  `TurnOffPhotograph` policy key as well as the older  `ShowContactPicture` registry key. The  `TurnOffPhotograph` policy key was introduced in Microsoft Outlook 2010, and  `ShowContactPicture` registry key was introduced in Microsoft Office Outlook 2007. The following table shows how these registry keys and **dispidShowSenderPhoto** interact. This setting does not turn on the display if administrator policy (  `TurnOffPhotograph` policy key) or user preference (  `ShowContactPicture` registry key) turns off the display. For more information about the  `TurnOffPhotograph` policy key, see [How to manage the Outlook Social Connector by using Group Policy](http://support.microsoft.com/kb/2020103). For more information about the  `ShowContactPicture` registry key, see [Deploying additional registry values in the Office Customization Tool for Outlook 2007](http://technet.microsoft.com/en-us/library/cc837949%28office.12%29.aspx).
  
|**Argument for method represented by **dispidShowSenderPhoto****|**`TurnOffPhotograph` policy key**|**`ShowContactPicture` registry key**|**Is picture displayed if present?**|
|:-----|:-----|:-----|:-----|
|True  <br/> |0 or not set  <br/> |1 or not set  <br/> |Yes  <br/> |
|True  <br/> |0 or not set  <br/> |0  <br/> |No  <br/> |
|True  <br/> |1  <br/> |1 or not set  <br/> |No  <br/> |
|True  <br/> |1  <br/> |0  <br/> |No  <br/> |
|False  <br/> |0 or not set  <br/> |1 or not set  <br/> |No  <br/> |
|False  <br/> |0 or not set  <br/> |0  <br/> |No  <br/> |
|False  <br/> |1  <br/> |1 or not set  <br/> |No  <br/> |
|False  <br/> |1  <br/> |0  <br/> |No  <br/> |
   
## See also

#### Concepts

[Constants (Outlook exported APIs)](constants-outlook-exported-apis.md)

