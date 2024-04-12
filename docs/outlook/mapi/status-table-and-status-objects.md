---
title: "Status Table and Status Objects"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 203765c1-4b08-4032-a5bf-18f3e752a899
 
 
---

# Status Table and Status Objects

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI provides a table with information about the status of the MAPI subsystem, MAPI spooler, address book, or a particular service provider. You can access this table by calling [IMAPISession::GetStatusTable](imapisession-getstatustable.md).
  
Each row in the status table represents a status object implemented by MAPI or a service provider. You can use a status object to display a provider's configuration property sheet, to change a provider password, to upload or download messages, and to communicate with a particular transport provider. 
  
There are two ways to access a status object:
  
- Through the status table
    
- Through a logon object's **OpenStatusEntry** method 
    
Because logon objects are unavailable to clients, you must use the status table to access status objects. The status table approach is indirect, requiring a few calls before the status object is opened and a pointer to its **IMAPIStatus** implementation returned. 
  
 **To use the status table to open a status object**
  
1. Call **IMAPIStatus::GetStatusTable** to retrieve an [IMAPITable](imapitableiunknown.md) pointer. 
    
2. Call the status table's [IMAPITable::SetColumns](imapitable-setcolumns.md) method to limit the column set to **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)), **PR_RESOURCE_TYPE** ([PidTagResourceType](pidtagresourcetype-canonical-property.md)), and **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)).
    
3. Limit the table view to a particular status object. For MAPI implementations, a client can define a property restriction using **PR_RESOURCE_TYPE**. For service provider implementations, a client can restrict on **PR_PROVIDER_DISPLAY** ([PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md)), the name of the provider, or on **PR_PROVIDER_DLL_NAME** ([PidTagProviderDllName](pidtagproviderdllname-canonical-property.md)), the name of the provider DLL file.
    
4. Call [IMAPITable::Restrict](imapitable-restrict.md) to set the restriction. 
    
5. Call [HrQueryAllRows](hrqueryallrows.md), passing in the [SPropertyRestriction](spropertyrestriction.md) structure, to retrieve the row that represents the status of the provider. 
    
6. Call [IMAPISession::OpenEntry](imapisession-openentry.md), specifying the entry identifier from the status table row, to open the status object and retrieve an **IMAPIStatus** pointer. 
    
To display a property sheet, call the status object's [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) method for the target provider. **SettingsDialog** displays a property sheet for viewing and in some cases, changing the configuration properties of a provider. 
  
To communicate with a transport provider, call its status object's [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method. **ValidateState** can reconfigure a transport provider, prevent the provider from displaying a user interface, and control a session that involves downloading message headers from a remote server, depending on the flags that you pass in. For example, to cancel the downloading of remote headers, pass the ABORT_XP_HEADER_OPERATION flag to **ValidateState**. To connect or disconnect from the remote server, pass FORCE_XP_CONNECT or FORCE_XP_DISCONNECT. To reconfigure the provider, pass CONFIG_CHANGED. 
  
Clients that implement sending or receiving of messages on demand call either a transport provider's or the MAPI spooler's [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md) method. You can pass three flags into the method: FLUSH_UPLOAD, FLUSH_DOWNLOAD, and FLUSH_FORCE. FLUSH_UPLOAD instructs the provider or the MAPI spooler to send any messages waiting in the output queue while FLUSH_DOWNLOAD instructs the provider or the MAPI spooler to receive any incoming messages. FLUSH_FORCE can be set with either of the other flags to cause the status object to perform the flush regardless of the timing. 
  
Do not expect to be able to call **SettingsDialog** or [ChangePassword](imapistatus-changepassword.md) on any of the MAPI subsystem, MAPI spooler, or address book status objects. Both the subsystem and address book status objects only support **ValidateState**; the MAPI spooler status object supports **FlushQueues** in addition to **ValidateState**.
  
## See also



[Status Tables](status-tables.md)
  
[MAPI Status Objects](mapi-status-objects.md)

