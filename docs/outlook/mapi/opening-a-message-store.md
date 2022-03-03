---
title: "Opening a message store"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 43b23fd7-999a-42c0-8f4d-47f5de266bdb
---

# Opening a message store

**Applies to**: Outlook 2013 | Outlook 2016 
  
Depending on the profile, a client will need to open one or more message stores during a typical session. Opening a message store means gaining access to a pointer to its [IMsgStore : IMAPIProp](imsgstoreimapiprop.md) implementation. The **IMsgStore** interface provides methods for notification, making folder assignments, and accessing folders and messages. 
  
Clients open message stores at logon and when a profile is being modified. If your client allows users to add message stores to the profile during an active session, you can either open them immediately or ignore them until the next session. By registering for notifications on the message store table, you will be alerted to the availability of a new message store.
  
To open a message store, you must have its entry identifier available. Most clients access the entry identifiers for the message stores they wish to open through the message store table. However, some message stores document the format of their entry identifiers, thereby enabling clients to bypass the message store table and construct the necessary entry identifier. They can pass this entry identifier directly to [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md) and MAPI automatically creates a profile section for the provider without associating it with any message service. 
  
## Retrieve an entry identifier from the message store table
  
1. Call [IMAPISession::GetMsgStoresTable](imapisession-getmsgstorestable.md) to open the message store table. 
    
2. Call **IMAPITable::SetColumns** to limit the table to a small column set that includes the following columns: 
    
   - **PR_PROVIDER_DISPLAY** or **PR_DISPLAY_NAME**
   - **PR_ENTRYID** properties 
   - **PR_MDB_PROVIDER**
   - **PR_RESOURCE_FLAGS**
    
3. Build a restriction to filter out the row that represents the message store to be opened. For more information about looking for the default message store, see [Opening the Default Message Store](opening-the-default-message-store.md). To look for a message store by name, apply any of the following property restrictions:
    
   - Match **PR_PROVIDER_DISPLAY** ([PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md)) with the general name for this type of message store. For example, PR_PROVIDER_DISPLAY might be set to "Personal Folders".
    
   - Match **PR_MDB_PROVIDER** ([PidTagStoreProvider](pidtagstoreprovider-canonical-property.md)) with the specific **MAPIUID** for this type of message store. 
    
   - Match **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) with the name for this particular message store. For example, **PR_DISPLAY_NAME** might be set to "My Messages for Fiscal Year 2010." 
    
4. Call [HrQueryAllRows](hrqueryallrows.md) to retrieve the appropriate row from the message store table. The entry identifier for the row will be included in the property value array for the **aRow** member of the row set pointed to by the  _pprows_ parameter. 
    
5. Call [FreeProws](freeprows.md) to free the row set pointed to by  _pprows_.
    
6. Release the message store table by calling its **IUnknown::Release** method. 
    
If you have created a custom entry identifier for the message store to be opened, call the [WrapStoreEntryID](wrapstoreentryid.md) function to convert it to a standard entry identifier. 
  
After you have a message store's entry identifier, call one of the following methods to open it:
  
- [IMAPISession::OpenMsgStore](imapisession-openmsgstore.md)
- [IMAPISession::OpenEntry](imapisession-openentry.md)
    
Call **OpenMsgStore** if you need to specify a variety of special options for the message store. **OpenMsgStore** allows you to suppress the display of dialog boxes, identify the message store as temporary or as a nonmessaging store, set access levels, and to defer errors. **OpenEntry** allows you only to set access levels and defer errors. 
  
Setting the MDB_NO_MAIL flag indicates to MAPI that the message store will not be used for sending or receiving messages. MAPI does not inform the MAPI spooler about the existence of this message store. The MDB_TEMPORARY flag designates a message store as temporary, implying that it cannot be used to store permanent information. Temporary message stores do not appear in the message store table. 
  
## See also

- [IMAPITable::SetColumns](imapitable-setcolumns.md)

