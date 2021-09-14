---
title: "Available events and their dispids (Outlook exported APIs)"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: 1fd848c7-038e-4e2f-8997-c8509b31df79
description: "This section describes the dispatch identifiers for the events that Outlook makes available."
---

# Available events and their dispids (Outlook exported APIs)

This section describes the dispatch identifiers for the events that Outlook makes available.
  
Outlook exposes the following dispatch identifiers (dispids) to allow C++ add-ins to listen to and handle the corresponding events from the [IDispatch::Invoke](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) function. 
  
|**Constant**|**Dispid for event**|**Description**|**Parameters**|**Remarks**|
|:-----|:-----|:-----|:-----|:-----|
|**dispidBeforePrint** <br/> |0xFC8E  <br/> |Used to handle the application-level event from the **IDispatch::Invoke** function that fires before a printing operation.  <br/> | There are 2 unnamed parameters:  <br/>  The first parameter is of the type **VT_BOOL|VT_BREF**. Return **VARIANT_TRUE** in this parameter to cancel the event.  <br/>  The second parameter is not used and should be ignored.  <br/> |This dispid is available since Outlook 2010.  <br/> |
|**dispidEventReadComplete** <br/> |0xFC8F  <br/> |Used to handle the item-level event from the **IDispatch::Invoke** function that fires when Outlook has completed reading the properties of the item.  <br/> |There is only one parameter  _Cancel_ which is of the type **VT_BOOL|VT_BREF**. Return **VARIANT_TRUE** in this parameter to cancel the read operation.  <br/> |This dispid is available since Outlook 2010.  <br/> This event corresponds to the Exchange Client Extensions (ECE) event **IExchExtMessageEvents::OnReadComplete**, and also to the **ReadComplete** event that has been added to the object model since Outlook 2013.  <br/> |
   
For an example of how to use a dispid to listen to and handle an event, see the  `CAppEventListener::Invoke` function in the C++ Outlook solution described in [Implementing Outlook 2002/XP Event Sinks in MFC C++ 2003 .NET](https://www.codeproject.com/Articles/4230/Implementing-Outlook-2002-XP-Event-Sinks-in-MFC-C).
  
## See also

- [Outlook exported APIs](outlook-exported-apis.md)
- [Constants (Outlook exported APIs)](constants-outlook-exported-apis.md)
- [About APIs exported by Outlook](about-apis-exported-by-outlook.md)
- [Implementing Outlook 2002/XP Event Sinks in MFC C++ 2003 .NET](https://www.codeproject.com/Articles/4230/Implementing-Outlook-2002-XP-Event-Sinks-in-MFC-C)

