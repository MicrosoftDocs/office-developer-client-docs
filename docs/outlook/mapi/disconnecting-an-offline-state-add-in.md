---
title: "Disconnecting an Offline State Add-in"
manager: soliver
ms.date: 12/7/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: 6922cb38-a9e3-e4a9-d4a3-e11b81fc77e2
description: "Last modified: December 07, 2015"
 
 
---

# Disconnecting an Offline State Add-in

 
  
**Applies to**: Outlook 
  
When the offline state add-in is disconnected, you must implement functions to properly terminate and clean up the add-in. For more information on setting up and using the offline state add-in to monitor connection state changes, see [Setting Up an Offline State Add-in](setting-up-an-offline-state-add-in.md) and [Monitoring Connection State Changes Using an Offline State Add-in](monitoring-connection-state-changes-using-an-offline-state-add-in.md).
  
 In this topic, these disconnection, terminate, and clean-up functions are demonstrated by using code examples from the Sample Offline State Add-in. The Sample Offline State Add-in is a COM add-in that adds an **Offline State** menu to Outlook and uses the Offline State API. Through the Offline State menu, you can enable or disable state monitoring, check the current state, and change the current state. For more information about downloading and installing the Sample Offline State Add-in, see [Installing the Sample Offline State Add-in](installing-the-sample-offline-state-add-in.md). For more information about the Offline State API, see [About the Offline State API](about-the-offline-state-api.md).
  
## On Disconnection Routine

The **IDTExtensibility2.OnDisconnection** method is called when the Offline State Add-in is unloaded. You should implement clean up code in this function. In the following example, the **IDTExtensibility2.OnDisconnection** function calls the  `HrTermAddin` function. 
  
## CMyAddin::OnDisconnection() Example

```
STDMETHODIMP CMyAddin::OnDisconnection(ext_DisconnectMode /*RemoveMode*/, SAFEARRAY * * /*custom*/) 
{ 
    Log(true,"OnDisconnection\n"); 
    HRESULT hRes = S_OK; 
    hRes = HrTermAddin(); 
     return hRes; 
}
```

## Terminate Add-in Function

The  `HrTermAddin` function calls the  `inDeInitMonitor`,  `HrRemoveMenuItems`, and  `UnloadLibraries` functions to finish cleaning up the Offline State Add-in. 
  
## CMyAddin::HrTermAddin()

```
HRESULT CMyAddin::HrTermAddin() 
{ 
    HRESULT hRes = S_OK; 
    DeInitMonitor(); 
    hRes =  HrRemoveMenuItems(); 
    UnloadLibraries(); 
    return hRes; 
}
```

## Deinitialize Monitor Routine

The  `inDeInitMonitor` function calls the [IMAPIOfflineMgr::Unadvise](imapiofflinemgr-unadvise.md) function to cancel the callbacks for the offline object. 
  
## DeInitMonitor() Example

```
void DeInitMonitor() 
{ 
Log(true,_T("Deinitializing Outlook Offline State Monitor\n")); 
HRESULT hRes = S_OK; 
if (g_lpOfflineMgr) 
{ 
hRes = g_lpOfflineMgr->Unadvise(MAPIOFFLINE_UNADVISE_DEFAULT, g_ulAdviseToken); 
g_lpOfflineMgr->Release(); 
g_lpOfflineMgr = NULL; 
g_ulAdviseToken = NULL; 
} 
}
```

## Remove Menu Items Routine

The  `HrRemoveMenuItems` function calls  `DispEventUnadvise` for each menu item under the **Offline State** menu, and then deletes the **Offline State** menu. 
  
## CMyAddin::HrRemoveMenuItems() Example

```
HRESULT CMyAddin::HrRemoveMenuItems() 
{     
    Log(true,"HrRemoveMenuItems\n"); 
    HRESULT hRes = S_OK; 
    if (m_fMenuItemsAdded) 
    { 
        try 
        { 
            if (m_spInitButton) 
            { 
                m_InitButtonHandler.DispEventUnadvise(m_spInitButton); 
            } 
            if (m_spDeinitButton) 
            { 
                m_DeinitButtonHandler.DispEventUnadvise(m_spDeinitButton); 
            } 
            if (m_spGetStateButton) 
            { 
                m_GetStateButtonHandler.DispEventUnadvise(m_spGetStateButton); 
            } 
            if (m_spSetStateButton) 
            { 
                m_SetStateButtonHandler.DispEventUnadvise(m_spSetStateButton); 
            } 
 
            m_spMyMenu->Delete(); 
        } 
        catch(_com_error) 
        { 
            hRes = E_FAIL; 
        } 
        if (SUCCEEDED(hRes)) 
        { 
            m_fMenuItemsAdded = false; 
        } 
    } 
    return hRes; 
}
```

## Unload Libraries Routine

When the add-in is unloaded from Outlook, the  `UnloadLibraries` function unloads the dynamic-link libraries (DLLs) that the add-in required. 
  
## UnloadLibraries() Example

```
void UnloadLibraries() 
{ 
    Log(true,_T("UnloadLibraries - freeing modules\n")); 
    pfnHrOpenOfflineObj = NULL; 
    pfnMAPIFreeBuffer = NULL; 
    if (hModMSMAPI) FreeLibrary(hModMSMAPI); 
    hModMSMAPI = NULL; 
    if (hModMAPI) FreeLibrary(hModMAPI); 
    hModMAPI = NULL; 
    if (hModMAPIStub) FreeLibrary(hModMAPIStub); 
    hModMAPIStub = NULL; 
}
```

## See also

#### Concepts

[About the Offline State API](about-the-offline-state-api.md)
  
[Installing the Sample Offline State Add-in](installing-the-sample-offline-state-add-in.md)
  
[About the Sample Offline State Add-in](about-the-sample-offline-state-add-in.md)
  
[Setting Up an Offline State Add-in](setting-up-an-offline-state-add-in.md)
  
[Monitoring Connection State Changes Using an Offline State Add-in](monitoring-connection-state-changes-using-an-offline-state-add-in.md)

