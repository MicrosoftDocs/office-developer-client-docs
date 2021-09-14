---
title: "About the Replication State Machine"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
ms.assetid: cf36c6cb-57b4-7b2b-e23d-e0bc8696de96
description: "Last modified: March 09, 2015"
 
 
---

# About the Replication State Machine

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This topic contains an overview of the state machine for Microsoft Outlook 2013 and Microsoft Outlook 2010 data replication.
  
> [!NOTE]
> The Replication API must be fully implemented according to the instructions in this topic in order to be useful or supported. The Replication API is available exclusively to replicate Outlook 2013 or Outlook 2010 changes to and from a server. 
  
## IOSTX and the State Machine

A client calls **[IOSTX::SyncBeg](iostx-syncbeg.md)**, **[IOSTX::SyncEnd](iostx-syncend.md)**, **[IOSTX::SyncHdrBeg](iostx-synchdrbeg.md)**, and **[IOSTX::SyncHdrEnd](iostx-synchdrend.md)** in a sequence to synchronize Outlook 2013 or Outlook 2010 folders and items between a local store and a server. The actual sequence of calls depends on the data that needs to be replicated (for example, a hierarchy of Outlook 2013 or Outlook 2010 folders, an Outlook 2013 or Outlook 2010 folder, mail items, calendar items, and so on) and the direction of synchronization (whether uploading from the local store to the server, or downloading from the server to the local store). Here is a typical sequence of calls: 
  
1. The client calls **IOSTX::SyncBeg** to begin replication, specifying a state identifier and a pointer to an address of a corresponding data structure. 
    
2. Outlook 2013 or Outlook 2010 allocates the data structure and initializes the data structure with the necessary information for the client. 
    
3. The client performs the replication, updating the data structure to convey to the local store any necessary information about the replication.
    
4. After performing the replication, the client calls **[IOSTX::SetSyncResult](iostx-setsyncresult.md)** and **IOSTX::SyncEnd** to notify the local store of the completion of the specific replication. 
    
> [!NOTE]
> The client always calls **IOSTX::SyncEnd** to end a replication that the client has begun for a certain state. Depending on the overall data that the client needs to synchronize, the client may call the pair of calls **IOSTX::SyncBeg** and **IOSTX::SyncEnd** more than once. 
  
## State Table

> [!NOTE]
> The following table lists all the valid states in the replication state machine, along with the corresponding state identifiers and data structures. In the **Data Replicated** column, the term "items" includes mail, calendar, contact, note, journal, and task items. When replicating changes from the local store to the server, use state identifiers specifying "UPLOAD" and data structures with the "UP" prefix (for example, **LR_SYNC_UPLOAD_HIERARCHY** and **[UPHIER](uphier.md)** ). When replicating changes from the server to the local store, use state identifiers specifying "DOWNLOAD" and data structures with the "DN" prefix (for example, **LR_SYNC_DOWNLOAD_HIERARCHY** and **[DNHIER](dnhier.md)** ). 
  
|||||
|:-----|:-----|:-----|:-----|
|**State** <br/> |**Data Replicated** <br/> |**State Identifier** <br/> |**Data Structure** <br/> |
|[Idle state](idle-state.md) <br/> | *None*  <br/> |**LR_SYNC_IDLE** <br/> | *None*  <br/> |
|[Synchronize state](synchronize-state.md) <br/> |Folders or items  <br/> |**LR_SYNC** <br/> |**[SYNC](sync.md)** <br/> |
|[Upload hierarchy state](upload-hierarchy-state.md) <br/> |Folders  <br/> |**LR_SYNC_UPLOAD_HIERARCHY** <br/> |**[UPHIER](uphier.md)** <br/> |
|[Upload folder state](upload-folder-state.md) <br/> |Folder  <br/> |**LR_SYNC_UPLOAD_FOLDER** <br/> |**[UPFLD](upfld.md)** <br/> |
|[Synchronize contents state](synchronize-contents-state.md) <br/> |Items  <br/> |**LR_SYNC_CONTENTS** <br/> |**[SYNCCONT](synccont.md)** <br/> |
|[Upload table state](upload-table-state.md) <br/> |Items  <br/> |**LR_SYNC_UPLOAD_TABLE** <br/> |**[UPTBL](uptbl.md)** <br/> |
|[Upload message state](upload-message-state.md) <br/> |Item  <br/> |**LR_SYNC_UPLOAD_MESSAGE** <br/> |**[UPMSG](upmsg.md)** <br/> |
|[Upload read status state](upload-read-status-state.md) <br/> |Items  <br/> |**LR_SYNC_UPLOAD_MESSAGE_READ** <br/> |**[UPREAD](upread.md)** <br/> |
|[Upload delete status state](upload-delete-status-state.md) <br/> |Items  <br/> |**LR_SYNC_UPLOAD_MESSAGE_DEL** <br/> |**[UPDEL](updel.md)** <br/> |
|[Download hierarchy state](download-hierarchy-state.md) <br/> |Folders  <br/> |**LR_SYNC_DOWNLOAD_HIERARCHY** <br/> |**[DNHIER](dnhier.md)** <br/> |
|[Download table state](download-table-state.md) <br/> |Items  <br/> |**LR_SYNC_DOWNLOAD_TABLE** <br/> |**[DNTBL](dntbl.md)** <br/> |
|[Download message header state](download-message-header-state.md) <br/> |Message header  <br/> |**LR_SYNC_DOWNLOAD_HEADER** <br/> |**[HDRSYNC](hdrsync.md)** <br/> |
   
## State Transition Diagram

The following diagram shows the state transitions that occur when uploading or performing a full synchronization (downloading followed by uploading) of folders or contents of folders (mail, calendar, contact, note, task, or journal items). 
  
@@@@@NEED TO INSERT ART HERE THAT IS MISSING@@@@@@
  
## Example: Uploading a Folder Hierarchy

 When uploading a hierarchy of folders, the following sequence of steps takes place: 
  
|||||
|:-----|:-----|:-----|:-----|
|**Step** <br/> |**Action** <br/> |**State** <br/> |**Related Data Structure** <br/> |
|1.  <br/> |The client initiates the hierarchy upload with **IOSTX::SyncBeg**.  <br/> |**LR_SYNC_UPLOAD_HIERARCHY** <br/> |**UPHIER** <br/> |
|2.  <br/> |Outlook 2013 or Outlook 2010 populates **UPHIER** with information for the client. This includes initializing the [out] parameters:  *iEnt*  is set to 0, and  *cEnt*  to the number of folders in the hierarchy that needs uploading.  <br/> |**LR_SYNC_UPLOAD_HIERARCHY** <br/> |**UPHIER** <br/> |
|3.  <br/> |The client does the actual hierarchy upload. As an example, if  *cEnt*  is 10, for each of the 10 folders, the client calls **IOSTX::SyncBeg**, specifying the appropriate state identifier and data structure for uploading a folder.  <br/> |**LR_SYNC_UPLOAD_FOLDER** <br/> |**UPFLD** <br/> |
|4.  <br/> |Outlook 2013 or Outlook 2010 populates **UPFLD** by initializing its [out] parameters, including the reason for the folder upload, the pointer to the folder object, and the entry ID for the folder.  <br/> |**LR_SYNC_UPLOAD_FOLDER** <br/> |**UPFLD** <br/> |
|5.  <br/> |The client uploads the specified folder.  <br/> |**LR_SYNC_UPLOAD_FOLDER** <br/> |**UPFLD** <br/> |
|6.  <br/> |The client notifies the local store of the completion of the folder upload: Upon success, the client sets the [in] parameter  *ulFlags*  in **UPFLD** with **UPF_OK**, and then calls **IOSTX::SetSyncResult (S_OK)** and **IOSTX::SyncEnd**. Upon failure, the client would not set  *ulFlags*  with the **UPF_OK** flag. It calls **IOSTX::SetSyncResult**, passing in the **HRESULT** value, and **IOSTX::SyncEnd**.  <br/> |**LR_SYNC_UPLOAD_FOLDER** <br/> |**UPFLD** <br/> |
|7.  <br/> |If **UPF_OK** is set, Outlook 2013 or Outlook 2010 will clear the internal request for uploading the folder. Then regardless of the state of  *ulFlags*  , it will clean up any internal bookkeeping information. While there are still folders in the hierarchy to upload (*iEnt*  is still less than  *cEnt*), the client and Outlook 2013 or Outlook 2010 repeat steps 3 through 7.  <br/> |**LR_SYNC_UPLOAD_FOLDER** <br/> |**UPFLD** <br/> |
|8.  <br/> |The client notifies the local store of the completion of the hierarchy upload: Upon success, the client sets the [in] flag in **UPHIER** with **UPH_OK**, and then calls **IOSTX::SetSyncResult (S_OK)** and **IOSTX::SyncEnd**. Upon failure, the client would not set the **UPH_OK** flag. It calls **IOSTX::SetSyncResult**, passing in the **HRESULT** value, and **IOSTX::SyncEnd**.  <br/> |**LR_SYNC_UPLOAD_HIERARCHY** <br/> |**UPHIER** <br/> |
|9.  <br/> |If **UPH_OK** is set, Outlook 2013 or Outlook 2010 will clear the internal request for uploading the hierarchy. Then regardless of the state of  *ulFlags*  , it will clean up any internal bookkeeping information.  <br/> |**LR_SYNC_UPLOAD_HIERARCHY** <br/> |**UPHIER** <br/> |
   
## See also



[About the Replication API](about-the-replication-api.md)
  
[MAPI Constants](mapi-constants.md)
  
[SYNCSTATE](syncstate.md)

