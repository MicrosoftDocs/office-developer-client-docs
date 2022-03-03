---
title: "Ending a MAPI Session"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: ca153737-75dc-426a-a410-7a7ab3264f23
 
 
---

# Ending a MAPI Session

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Clients can end their sessions in response to a user's request, either immediately or after all outbound messages have been processed, and when a critical error occurs. Some clients need to stay logged on so that pending outbound messages can reach the transport provider and the destination messaging system. If such a client sends a message and immediately logs off, the message may remain in the outgoing queue until a user logs back on and stays logged on long enough for the message to be transmitted.
  
 **When you need to terminate your session with the MAPI subsystem**
  
1. Cancel the registrations for all notifications by calling the **Unadvise** method of every registered object. 
    
2. Release all open objects by calling their [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28VS.85%29.aspx) methods. The types of open objects can include advise sinks, the status table, the Outbox folder, one or more message stores, and the address book. 
    
3. Call [MAPIFreeBuffer](mapifreebuffer.md) to free the memory for any cached entry identifiers, such as **PR_IPM_SUBTREE_ENTRYID** ([PidTagIpmSubtreeEntryId](pidtagipmsubtreeentryid-canonical-property.md)).
    
4. Call [IMAPISession::Logoff](imapisession-logoff.md), setting the MAPI_LOGOFF_UI flag if you allow a user interface and the MAPI_LOGOFF_SHARED flag if you own the current shared session. **Logoff** notifies all other clients that are using the current shared session that they should log off by sending an error notification. 
    
5. Release the session pointer by calling the session's **IUnknown::Release** method. 
    
6. If you called [OleInitialize](https://msdn.microsoft.com/library/ms690134%28v=VS.85%29.aspx) during session startup to initialize the OLE libraries, uninitialize them now by calling [OleUninitialize](https://msdn.microsoft.com/library/ms691326%28VS.85%29.aspx). Only clients that have called **OleInitialize** must call **OleUninitialize**. 
    
7. Uninitialize the MAPI libraries by calling [MAPIUninitialize](mapiuninitialize.md). If you called **OleInitialize** at some point, make sure that a call to **OleUninitialize** occurs before this call to **MAPIUninitialize**. The timing is crucial. If the call to **OleUninitialize** follows the call to **MAPIUninitialize**, your client might terminate ungracefully. 
    
8. If you called [ScInitMapiUtil](scinitmapiutil.md) during session startup to initialize the MAPI utility library, uninitialize it now by calling [DeinitMapiUtil](deinitmapiutil.md). Only clients that have called **ScInitMapiUtil** must call **DeinitMapiUtil**.
    
> [!NOTE]
> All open objects must be released before the call to **IMAPISession::Logoff**. Objects that remain open after **Logoff** is called become invalid; they cannot accept any calls and might never be freed. If a call is made to one of these objects, expect the call to fail. 
  
 MAPI has no mechanism for deleting DLLs during the session shutdown process. A service provider's DLL can only be deleted when a configuration client such as the Control Panel calls its message service entry point function with the MSG_SERVICE_INSTALL event. 
  

