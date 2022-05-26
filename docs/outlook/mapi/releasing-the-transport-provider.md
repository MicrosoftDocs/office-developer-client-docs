---
title: "Releasing the Transport Provider"
description: Outlines the steps when MAPI or the MAPI spooler finishes using a transport logon object. This topic applies to Outlook 2013 and Outlook 2016.
manager: soliver
ms.date: 12/07/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: e0f37485-55c9-40f0-bc8c-48f7297f9f50
 
 
---

# Releasing the Transport Provider

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
When MAPI or the MAPI spooler finishes using a transport logon object:
  
1. MAPI or the MAPI spooler calls the transport provider's [IXPLogon::TransportLogoff](ixplogon-transportlogoff.md) method. 
    
2. The transport provider invalidates the status object by calling the [IMAPISupport::MakeInvalid](imapisupport-makeinvalid.md) method. Whether the transport provider invalidates message objects that are being sent or received at the time of the **TransportLogoff** call depends on the flags that were passed to **TransportLogoff**.
    
3. The transport provider calls the support object's [IUnknown::Release](https://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) method to remove the transport provider's row from the status table and remove from internal tables any unique identifiers (UIDs) that were set with the [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) method. It decrements the count of known logon objects active on this provider object. If the count reaches zero, MAPI calls the [IXPProvider::Shutdown](ixpprovider-shutdown.md) method and **Release** on the provider object. If this was the last known provider object using this DLL on this process, MAPI calls the **FreeLibrary** function on the DLL at a later time. Memory for the MAPI support object is freed and the support object **Release** method returns. 
    
4. The **TransportLogoff** method returns S_OK. 
    
5. MAPI or the MAPI spooler calls **Release** on the transport provider's logon object. The memory for the object is released. 
    
6. MAPI or the MAPI spooler calls **FreeLibrary** on the provider DLL. 
    
For robustness, the logon and provider objects should be able to handle final **Release** calls on themselves without first having their **TransportLogoff** or **Shutdown** methods called. If **Release** is called in such cases, transport providers should treat the calls as if **TransportLogoff** or **Shutdown** had been called with a zero argument followed by **Release**.
  

