---
title: "Available events and their dispids (Outlook exported APIs)"
manager: lindalu
ms.date: 02/09/2022
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 1fd848c7-038e-4e2f-8997-c8509b31df79
description: "Describes the dispatch identifiers for the events that Outlook makes available."
---

# Available events and their dispids (Outlook exported APIs)

This section describes the dispatch identifiers for the events that Outlook makes available.
  
Outlook exposes the following dispatch identifiers (dispids) to allow C++ add-ins to listen to and handle the corresponding events from the IDispatch::Invoke <!--(/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke.md)--> function.
  
|**Constant**|**Dispid for event**|**Description**|**Parameters**|**Remarks**|
|:-----|:-----|:-----|:-----|:-----|
|**dispidBeforePrint**  |0xFC8E  |Used to handle the application-level event from the **IDispatch::Invoke** function that fires before a printing operation. | There are 2 unnamed parameters:    The first parameter is of the type **VT_BOOL\|VT_BREF**. Return **VARIANT_TRUE** in this parameter to cancel the event.  The second parameter is not used and should be ignored. |This dispid is available since Outlook 2010. |
|**dispidEventReadComplete**  |0xFC8F  |Used to handle the item-level event from the **IDispatch::Invoke** function that fires when Outlook has completed reading the properties of the item. |There is only one parameter _Cancel_ which is of the type **VT_BOOL\|VT_BREF**. Return **VARIANT_TRUE** in this parameter to cancel the read operation. |This dispid is available since Outlook 2010. This event corresponds to the Exchange Client Extensions (ECE) event **IExchExtMessageEvents::OnReadComplete**, and also to the **ReadComplete** event that has been added to the object model since Outlook 2013. |

For an example of how to use a dispid to listen to and handle an event, see the `CAppEventListener::Invoke` function in the C++ Outlook solution described in [Implementing Outlook 2002/XP Event Sinks in MFC C++ 2003 .NET](https://www.codeproject.com/Articles/4230/Implementing-Outlook-2002-XP-Event-Sinks-in-MFC-C).
  
## See also

- [Outlook exported APIs](outlook-exported-apis.md)
- [Constants (Outlook exported APIs)](constants-outlook-exported-apis.md)
- [About APIs exported by Outlook](about-apis-exported-by-outlook.md)
- [Implementing Outlook 2002/XP Event Sinks in MFC C++ 2003 .NET](https://www.codeproject.com/Articles/4230/Implementing-Outlook-2002-XP-Event-Sinks-in-MFC-C)
