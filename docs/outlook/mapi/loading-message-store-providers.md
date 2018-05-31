---
title: "Loading Message Store Providers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 632d3ef9-43c5-429a-84d7-2dce543d49fb
description: "Last modified: July 23, 2011"
 
 
---

# Loading Message Store Providers

  
  
**Applies to**: Outlook 
  
When a client application opens a message store, MAPI loads the message store provider's DLL into memory. After MAPI loads the DLL, a very specific sequence of method calls occurs between the message store provider and MAPI. This method call sequence enables MAPI to get top-level [IMSProvider : IUnknown](imsprovideriunknown.md), [IMSLogon : IUnknown](imslogoniunknown.md), and [IMsgStore : IMAPIProp](imsgstoreimapiprop.md) interfaces, and allows the message store provider to get a MAPI support object. After the call sequence, the message store provider should be ready to accept logons from clients. 
  
The call sequence when a message provider DLL is loaded is as follows:
  
1. The client calls [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md).
    
2. If the message store is not already open, MAPI loads the store provider's DLL and calls the DLL's [MSProviderInit](msproviderinit.md) entry point. If the message store is already open, MAPI skips steps 2 and 3, and then uses the existing [IMSProvider : IUnknown](imsprovideriunknown.md) interface to complete step 4. 
    
3. **MSProviderInit** creates and returns an **IMSProvider** object. 
    
4. MAPI calls [IMSProvider::Logon](imsprovider-logon.md), passing the client application's message store entry identifier.
    
5. **IMSProvider::Logon** creates and returns an [IMSLogon : IUnknown](imslogoniunknown.md) interface and an [IMsgStore : IMAPIProp](imsgstoreimapiprop.md) interface, and then calls the [IUnknown::AddRef](http://msdn.microsoft.com/library/b4316efd-73d4-4995-b898-8025a316ba63%28Office.15%29.aspx) method on its [IMAPISupport : IUnknown](imapisupportiunknown.md) interface. If the client's message store entry identifier refers to a message store that is already open, the message store provider can return existing **IMSLogon** and **IMsgStore** interfaces and does not need to call **AddRef** on its support object. 
    
6. If the client did not set the MAPI_NO_MAIL flag when it logged on and it did not set the MDB_NO_MAIL in step 1, MAPI gives the message store's entry identifier to the MAPI spooler so the MAPI spooler can log on to the message store.
    
7. MAPI returns the **IMsgStore** interface to the client. 
    
8. The MAPI spooler calls [IMSProvider::SpoolerLogon](imsprovider-spoolerlogon.md).
    
9. **IMSProvider::SpoolerLogon** returns the same **IMSLogon** and **IMsgStore** interfaces from step 5. 
    
> [!NOTE]
> If the logon call to the message store provider fails because an incorrect password was supplied and the message store provider cannot display an interface to ask for the correct password, it should return MAPI_E_FAILONEPROVIDER from the **IMSProvider::Logon** method. This will allow clients to prompt the user for a password to try logging on to the message store provider again instead of causing MAPI to fail the provider for the entire session. 
  
## See also



[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

