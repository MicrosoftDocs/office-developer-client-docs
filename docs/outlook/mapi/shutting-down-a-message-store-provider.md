---
title: "Shutting Down a Message Store Provider"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: e38219db-f867-4c1d-9973-0e025779e8b6
 
 
---

# Shutting Down a Message Store Provider

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
If your provider is a message store provider, it can be shut down in one of the following ways:
  
- When a client or the MAPI spooler calls [IMsgStore::StoreLogoff](imsgstore-storelogoff.md). Shutting down a message store provider with **StoreLogoff** causes the shutdown to occur in an orderly and controlled manner. 
    
- When a client calls [IMAPISession::Logoff](imapisession-logoff.md). 
    
Your implementation of **IMsgStore::StoreLogoff** should begin by calling [IMAPISupport::StoreLogoffTransports](imapisupport-storelogofftransports.md) to inform MAPI that it is being shut down, indicating that any related transport providers should be logged off. When **IMsgStore::StoreLogoff** returns, its caller invokes your message store's [IUnknown::Release](https://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) method. Implement this **Release** method by calling the support object's **IUnknown::Release** method. 
  
MAPI performs the following tasks in its implementation of **IUnknown::Release** for message stores: 
  
1. Removes all of the [MAPIUID](mapiuid.md) structures registered by the message store provider. 
    
2. Removes the message store provider's row from the status table.
    
3. Calls [IMSLogon::Logoff](imslogon-logoff.md) to release all open objects, subobjects, and status objects. 
    
4. Calls [IUnknown::Release](https://msdn.microsoft.com/library/4b494c6f-f0ee-4c35-ae45-ed956f40dc7a%28Office.15%29.aspx) to release the message store provider's logon object. 
    
Some clients might omit the call to **IMsgStore::StoreLogoff**, initiating the shutdown of your message store provider with the call to the message store's **IUnknown::Release** method. A shutdown under these circumstances without the call to **StoreLogoff** is less orderly and controlled. Write your message store's **Release** method to handle this possibility and keep track of whether or not a call to **IMAPISupport::StoreLogoffTransports** has occurred. **StoreLogoffTransports** must be called once during the shutdown process. If you detect in your **Release** method that **StoreLogoffTransports** has not yet been called, invoke it with the LOGOFF_ABORT flag. 
  
## See also



[Shutting Down a Service Provider](shutting-down-a-service-provider.md)

