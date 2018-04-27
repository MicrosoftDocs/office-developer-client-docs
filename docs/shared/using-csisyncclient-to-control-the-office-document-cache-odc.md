---
title: "Using CSISyncClient to control the Office Document Cache (ODC)"
 
 
manager: soliver
ms.date: 7/13/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 394b8e6f-9132-4c98-8fd6-46ad3c871440
description: "Learn how to use CSISyncClient to control the Office Document Cache (ODC)."
---

# Using CSISyncClient to control the Office Document Cache (ODC)

Learn how to use CSISyncClient to control the Office Document Cache (ODC).
  
CSISyncClient is an out-of-proc COM server (CsiSyncClient.exe) that allows Microsoft OneDrive to control the behavior of the Office Document Cache (ODC). For example, OneDrive may call upon the ODC via CSISyncClient to upload and download files to and from MS-FSSHTTP enabled endpoints. This enables advanced service-backed features in Office, such as co-authoring and seamless transitions from offline to online.
  
CsiSyncClient is available in Office Desktop (both x86 and x64). Note: While newer versions of Office may ship with CsiSyncClient, the process will be used for backward compatibility only. The CsiSyncClient interface and the methodology of controlling the ODC will change in future versions of Office.
  
The class ID is currently set to respond only to OneDrive.
  
The COM object is usable as an out-of-proc COM server and runs in CsiSyncClient.exe. Due to limitations with Access (which the ODC uses), it ships with the bit type that Office comes in, so x64 Office means an x64 COM object, or x86 Office means an x86 COM object. To get around this limitation, specifying CLSCTX_LOCAL_SERVER as part of the CoCreateInstance will have the COM object be hosted as an out-of-proc COM server, allowing cross-bitness compatibility.
  
## Interfaces

CSISyncClient uses the following interfaces.
  
### Interface ILSCLocalSyncClient

This is the primary interface used to synchronize files in Office.
  
||
|:-----|
|ProgID: Office.LocalSyncClient  <br/> CLSID: {14286318-B6CF-49a1-81FC-D74AD94902F9}  <br/> TypeLib: {66CDD37F-D313-4e81-8C31-4198F3E42C3C}  <br/> |
   
The COM object that is exposed is used as an out-of-proc server. Specifying CLSCTX_LOCAL_SERVER as part of CoCreateInstance allows compatability between 64bit and 32bit processes.
  
Once you've co-created the COM object, you MUST call [ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) first. Once [ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has completed successfully, you may call any API as often as you wish and in any order. You may also call [ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) on an already initialized object, but this does nothing. 
  
The exceptions to the previous paragraph are [ILSCLocalSyncClient::ResetCache ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_ResetCache) and [ILSCLocalSyncClient::Uninitialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Uninitialize). After you call [ILSCLocalSyncClient::Uninitialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Uninitialize) on the COM object, you MUST destroy that object and create a new one. [ILSCLocalSyncClient::ResetCache ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_ResetCache) will delete your subcache, delete all associated file information in the cache, but leave the documents on disk. It also leaves the state intact for communicating with the cache. This allows you to call [ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) again to create a new cache without having to destroy and recreate the COM object. 
  
#### Public Member Functions

#### ILSCLocalSyncClient::DeleteFile

DeleteFile is used to remove the file information from the cache. However, this method will leave the associated file on disk and on the server.
  
HRESULT ILSCLocalSyncClient::DeleteFile ( [in] BSTR bstrResourceID )
#### Parameters

 _bstrResourceID_
  
The string which identifies the ResourceID of the file. This value must be non-empty with a maximum of 128 characters. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_FAIL  <br/> |The call failed.  <br/> |
|E_LSC_FILENOTFOUND  <br/> |The given ResourceID is not in the cache.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |Initialize has not been successfully called in the past.  <br/> |
|E_LSC_PENDINGCHANGESINCACHE  <br/> |The file is currently synchronizing or open and cannot be deleted.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::GetChanges
<a name="ILSCLocalSyncClient_GetChanges"> </a>

GetChanges returns an enumerator of ILSCEvent objects, and also returns a token that is given to the next call to GetChanges, assuming the consumer has processed the previous set of events. Events before the  _nPreviousChangesToken_ specified will be deleted and unavailable. If there are no events to be processed,  _pnCurrentChangesToken_ should be the same value as  _nPreviousChangesToken_, but  _ppiEvents_ will still be set. 
  
HRESULT ILSCLocalSyncClient::GetChanges ( [in] LONG nPreviousChangesToken, [out] LONG \* pnCurrentChangesToken, [out] IEnumLSCEvent \*\* ppiEvents )
#### Parameters

 _nPreviousChangesToken_
  
Identifies which event was last processed by the consumer. 
  
 _pnCurrentChangesToken_
  
Identifies the most recent event being handed to the consumer. Must not be null.
  
 _ppiEvents_
  
An enumerator for the events handed to the consumer. Must not be null. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::GetClientNetworkSyncPermission
<a name="ILSCLocalSyncClient_GetChanges"> </a>

GetClientNetworkSyncPermission is used to query whether Office's synchronizing heuristics for network cost and power usage are overridden. When on a 3G or other high cost network, or when running on battery versus being plugged in, Office may choose to block network traffic until a more opportune time.
  
HRESULT ILSCLocalSyncClient::GetClientNetworkSyncPermission ( [in] LSCNetworkSyncPermissionType nspType, [out] VARIANT_BOOL \* pfSyncEnabled )
#### Parameters

 _nspType_
  
A flag which defines which cost heuristic to query. See [Enum LSCNetworkSyncPermissionType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCNetworkSyncPermissionType). 
  
 _pfSyncEnabled_
  
Specifies whether the requested cost heuristic is currently overridden or not. Must not be null. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::GetFileStatus
<a name="ILSCLocalSyncClient_GetChanges"> </a>

GetFileStatus is used to gather information for a specific file: whether it exists in the cache, if it has pending communication with the server copy, and if Office 2013 has the most up to date data from the local copy. It requires a bitwise flag of [Enum LSCStatusFlag](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCStatusFlag) values to determine what information the CsiSyncClient COM object is to query for. 
  
HRESULT ILSCLocalSyncClient::GetFileStatus ( [in] BSTR bstrResourceID, [in] LSCStatusFlag sfRequestedStatus, [out] BSTR \* pbstrFileSystemPath, [out] BSTR \* pbstrETag, [out] LSCStatusFlag \* psfFileStatus )
#### Parameters

 _bstrResourceID_
  
The string which identifies the file on the client. This value must be non-empty, with a maximum of 128 characters. 
  
 _sfRequestedStatus_
  
A flag which defines what information to return. See [Enum LSCStatusFlag](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCStatusFlag). 
  
 _pbstrFileSystemPath_
  
The string which identifies the location of the file identified by  _bstrResourceID_ on the client. Must not be null. 
  
 _pbstrETag_
  
A string which will contain the eTag for the file identified by  _bstrResourceID_. Must not be null. 
  
 _psfFileStatus_
  
A flag which will contain the status requested via  _sfRequestedStatus_ for the file identified by  _bstrResourceID_. Must not be null. See [Enum LSCStatusFlag](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCStatusFlag). 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_FILENOTFOUND  <br/> |The file information specified by  _bstrResourceID_ does not exist in the cache.  <br/> |
|E_LSC_LOCALFILEUNAVAILABLE  <br/> |LSCStatusFlag_LocalFileUnchanged was requested or the file specified by  _bstrResourceID_ is locked or missing.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::GetSupportedFileExtensions
<a name="ILSCLocalSyncClient_GetSupportedFileExtensions"> </a>

GetSupportedFileExtensions returns a list of pipe-delimited file extensions which are currently supported by the CsiSyncClient COM object. Note that this list may change, and the consumer will be notified of a change via the IPartnerActivityCallback object provided on [ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) (See EventOccured). 
  
An example of the string returned is as follows: "|docx|docm|pptx|"
  
HRESULT ILSCLocalSyncClient::GetSupportedFileExtensions ( [out] BSTR \* pbstrSupportedFileExtensions )
#### Parameters

 _pbstrSupportedFileExtensions_
  
A string to be set with a pipe-delimited set of file extensions supported by the CsiSyncClient COM object. Must not be null. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::Initialize
<a name="ILSCLocalSyncClient_Initialize"> </a>

Initialize must be the first method called. Otherwise, all other APIs will return E_LSC_NOTINITIALIZED. Calling Initialize on an already initialized object returns S_OK and does nothing. If E_LSC_CACHEMISMATCH is returned, the caller may call [ILSCLocalSyncClient::ResetCache ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_ResetCache) to delete the cache associated with the given SuppliedID. However, in this case other APIs will still return E_LSC_NOTINITIALIZED. 
  
HRESULT ILSCLocalSyncClient::Initialize ( [in] BSTR bstrSuppliedID, [in] BSTR bstrProgID, [in] BSTR bstrFileSystemDirectoryHint, [in] IPartnerActivityCallback \* pEventCallback, [out] VARIANT_BOOL \* pfCreatedNewCache )
#### Parameters

 _bstrSuppliedID_
  
Identifies the consumer and which cache to use. Must be non-empty with a maximum of 32 characters. 
  
 _bstrProgID_
  
Identifies the consumer's COM object for two-way communication. Must be non-empty with a maximum of 39 characters. See [\<ProgID\> Key](http://msdn.microsoft.com/en-us/library/ms690196.aspx.aspx) for more information on ProgIDs. 
  
 _bstrFileSystemDirectoryHint_
  
Identifies the directory root in which local files will be stored. Must be non-empty with a maximum of 256 characters. The directory must already exist. 
  
 _pEventCallback_
  
The callback interface which CsiSyncClient will notify on changes. See IPartnerActivityCallback::EventOccurred. This value must not be null. 
  
 _pfCreatedNewCache_
  
Returns whether a new cache was created. If no cache is associated with the SuppliedID, one will be created. This value must not be null.
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_CACHEMISMATCH  <br/> |A SuppliedID already has a cache associated with it, but has a different ProgId or FileSystemDirectoryHint than the ones provided.  <br/> |
|E_LSC_DIRECTORYHINTCONFLICT  <br/> |The FileSystemDirectoryHint (or a subfolder) already exists on a different cache.  <br/> |
|E_LAC_PROGIDCONFLICT  <br/> |The ProgID already exists on a different cache.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::LocalFileChange
<a name="ILSCLocalSyncClient_LocalFileChange"> </a>

LocalFileChange is used to tell the CsiSyncClient COM object to attempt to upload the specified file. The method will prepare the file for upload, including reading the file's current contents. If an upload is already pending, the previous upload will be discarded and the new contents prepared for upload. If the file is open for editing in an application, this method will return S_OK without preparing the file for upload (the application should already do this step if there are changes).
  
This method will allow uploads if it was marked as uploads blocked previously (see [ILSCLocalSyncClient::RenameFile ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_RenameFile)).
  
HRESULT ILSCLocalSyncClient::LocalFileChange ( [in] BSTR bstrFileSystemPath, [in] BSTR bstrWebPath, [in] BSTR bstrResourceID )
#### Parameters

 _bstrFileSystemPath_
  
A string which identifies the file on the client. This value must be a non-empty local path with a maximum of 256 characters. This path must be in the directory tree specified by the FileSystemDirectoryHint when the call to [ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) was made. 
  
 _bstrResourceID_
  
A string which identifies the ResourceID of the file. This value must be non-empty with a maximum of 128 characters. 
  
 _bstrWebPath_
  
A string which identifies the file on the server. This value must be non-empty, valid URL, but no longer than INTERNET_MAX_URL_LENGTH, as defined by http://support.microsoft.com/kb/208427. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_CONFLICTINGFILE  <br/> |The file specified by  _bstrFileSystemPath_ has a different ResourceID than specified. An event of type LSCEventType_OnFilePathConflict is sent when this error is returned. See [ILSCLocalSyncClient::GetChanges ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_GetChanges).  <br/> |
|E_LSC_FILENOTFOUND  <br/> |The file was deleted mid-operation.  <br/> |
|E_LSC_FILENOTSUPPORTED  <br/> |The given file extension is not supported by the CsiSyncClient COM object. See [ILSCLocalSyncClient::GetSupportedFileExtensions ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_GetSupportedFileExtensions).  <br/> |
|E_LSC_FILEUPTODATE  <br/> |The COM object did not schedule an upload because the file in the cache had the most recent changes from the disk.  <br/> |
|E_LSC_LOCALFILEUNAVAILABLE  <br/> |The file specified by  _bstrFileSystemPath_ is missing or locked.  <br/> |
|E_LSC_LOCALPATHNOTMAPPED  <br/> |The given FileSystemPath is not under the directory root specified by the FileSystemDirectoryHint when the call to Initialize was made.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|E_LSC_PATHMISMATCH  <br/> |The file specified by  _bstrResourceID_ has a different FileSystemPath than specified.  <br/> |
|E_LSC_PENDINGCHANGESINCACHE  <br/> |The file specified already has pending changes in a different cache and cannot yet be associated with the consumer's cache.  <br/> |
|E_LSC_SERVERPATHINDIFFERENTCACHE  <br/> |The WebPath provided falls under a different cache.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::RenameFile
<a name="ILSCLocalSyncClient_RenameFile"> </a>

RenameFile will associate a new URL and local path for a given ResourceID. If the file specified by the ResourceID doesn't already exist in the cache, an attempt will be made to create it and mark it for download.
  
HRESULT ILSCLocalSyncClient::RenameFile ( [in] BSTR bstrResourceID, [in] BSTR bstrNewFileSystemPath, [in] BSTR bstrNewWebPath, [in] VARIANT_BOOL fBlockUploads )
#### Parameters

 _bstrResourceID_
  
A string which identifies the ResourceID of the file. This value must be non-empty with a maximum of 128 characters. 
  
 _bstrNewFileSystemPath_
  
A string which specifies the new local path for the file. This value must be a non-empty local path with a maximum of 256 characters. This path must be in the directory tree specified by the FileSystemDirectoryHint when the call to Initialize was made. 
  
 _bstrNewWebPath_
  
A string which specifies the new URL for the file. This value must be non-empty valid URL, but no longer than INTERNET_MAX_URL_LENGTH, as defined by http://support.microsoft.com/kb/208427. 
  
 _fBlockUploads_
  
Specifies whether uploads to the new location are allowed currently. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_CONFLICTINGFILE  <br/> |The  _bstrNewFileSystemPath_ or  _bstrNewWebPath_ already exist on another file in any cache. An event of type LSCEventType_OnFilePathConflict is sent when this error is returned. See [ILSCLocalSyncClient::GetChanges ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_GetChanges).  <br/> |
|E_LSC_FILENOTFOUND  <br/> |The file information was deleted from the cache while this method was running.  <br/> |
|E_LSC_LOCALPATHNOTMAPPED  <br/> |The given FileSystemPath is not under the directory root specified by the FileSystemDirectoryHint when the call to Initialize was made.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|E_LSC_PENDINGCHANGESINCACHE  <br/> |The file specified is currently synchronizing in an Office application.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::ResetCache
<a name="ILSCLocalSyncClient_ResetCache"> </a>

ResetCache will delete the cache associated with the SuppliedID that was provided on Initialize. This includes all of the file information, but will leave the files on both the client and the server. This method also leaves the object in a partially uninitialized state. The only valid calls after this are [ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) or [ILSCLocalSyncClient::Uninitialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Uninitialize). This method MAY be called if Initialize fails and returns E_LSC_CACHEMISMATCH, and will delete the cache associated with the SuppliedID that was provided with the failing call.
  
HRESULT ILSCLocalSyncClient::ResetCache( )
#### Parameters

None
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |The call failed.  <br/> |
|E_LSC_NOTINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) was not successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::ServerFileChange
<a name="ILSCLocalSyncClient_ServerFileChange"> </a>

ServerFileChange tells the CsiSyncClient COM object to mark the specified file for download. If the file is open in an Office application for edit, this method will return S_OK without marking the file for download (the application should already do this step if there are changes).
  
This method will allow downloads if it was marked as downloads blocked previously (see RenameFile).
  
HRESULT ILSCLocalSyncClient::ServerFileChange ( [in] BSTR bstrFileSystemPath, [in] BSTR bstrWebPath, [in] BSTR bstrResourceID )
#### Parameters

|
|
|**Parameter**|**Description**|
|:-----|:-----|
|bstrFileSystemPath  <br/> |A string which identifies the file on the client. This value must be a non-empty local path with a maximum of 256 characters. This path must be in the directory tree specified by the FileSystemDirectoryHint when the call to Initialize was made.  <br/> |
|bstrResourceID  <br/> |A string which identifies the ResourceID of the file. This value must be non-empty with a maximum of 128 characters.  <br/> |
|bstrWebPath  <br/> |A string which identifies the file on the server. This value must be a non-empty valid URL, but no longer than INTERNET_MAX_URL_LENGTH, as defined by http://support.microsoft.com/kb/208427.  <br/> |
   
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |Failure to set the cache connectivity state.  <br/> |
|E_LSC_CONFLICTINGFILE  <br/> |The file specified by  _bstrFileSystemPath_ has a different ResourceID than specified.  <br/> |
|E_LSC_FILENOTSUPPORTED  <br/> |The given file extension is not supported by the CsiSyncClient COM object. See GetSupportedFileExtensions.  <br/> |
|E_LSC_FILENOTFOUND  <br/> |The file was deleted in mid-operation.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_LOCALPATHNOTMAPPED  <br/> |The given FileSystemPath is not under the directory root specified by the FileSystemDirectoryHint when the call to Initialize was made.  <br/> |
|E_LSC_NOINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|E_LSC_PATHMISMATCH  <br/> |The file specified by  _bstrResourceID_ has a different FileSystemPath than specified.  <br/> |
|E_LSC_PENDINGCHANGESINCACHE  <br/> |The specified file already has pending changes in a different cache and cannot yet be associated with the consumer's cache.  <br/> |
|E_LSC_SERVERPATHINDIFFERENTCACHE  <br/> |The WebPath provided falls under a different cache.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::SetClientConnectivityState
<a name="ILSCLocalSyncClient_ServerFileChange"> </a>

Sets the cache into an online or offline state. If offline, Office will not attempt to communicate with the server for any files in that cache, regardless of each individual file's  _fBlockUploads_ setting. 
  
HRESULT ILSCLocalSyncClient::SetClientConnectivityState ( [in] VARIANT_BOOL fIsOnline )
#### Parameters

 _fIsOnline_
  
A boolean determining the connectivity state of the cache. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |Failure to set the cache connectivity state.  <br/> |
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|E_LSC_NOINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::SetClientNetworkSyncPermission
<a name="ILSCLocalSyncClient_ServerFileChange"> </a>

SetClientNetworkSyncPermission is used to either override or restoreOffice's synchronizing heuristics for network cost and power usage. When on a 3G or other high cost network, or when running on battery versus being plugged in, Office may choose to block network traffic until a more opportune time. The consumer of this API can use it to override Office's heuristics and force synchronizing to occur.
  
HRESULT ILSCLocalSyncClient::SetClientNetworkSyncPermission ( [in] LSCNetworkSyncPermissionType nspType, [in] VARIANT_BOOL fEnableSync )
#### Parameters

 _nspType_
  
A flag which defines which cost heuristic to override. See [Enum LSCNetworkSyncPermissionType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCNetworkSyncPermissionType).
  
 _fEnableSync_
  
Specifies whether to force synchronizing on, thus overriding that cost heuristic, or to no longer override it. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |Failure to override synchronizing heuristics.  <br/> |
|E_LSC_NOINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
#### ILSCLocalSyncClient::Uninitialize
<a name="ILSCLocalSyncClient_Uninitialize"> </a>

Unloads the cache from the COM object and perform closing operations. [ILSCLocalSyncClient::Uninitialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Uninitialize) MUST be called before destroying the COM object. Once called, no other APIs can be called, the COM object MUST be destroyed and a new one created if you wish to continue operations. 
  
HRESULT ILSCLocalSyncClient::Uninitialize ( )
#### Parameters

None.
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |Failure to uninitialize.  <br/> |
|E_LSC_NOINITIALIZED  <br/> |[ILSCLocalSyncClient::Initialize ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_Initialize) has not been successfully called in the past.  <br/> |
|S_OK  <br/> |The call succeeded.  <br/> |
   
### Interface IEnumLSCEvent

This interface represents a list of ILSCEvent events.
  
#### Public Member Functions

#### IEnumLSCEvent::FNext

Retrieves the next event from the list of events.
  
HRESULT IEnumLSCEvent::FNext ( [out] ILSCEvent \*\* ppiLSCEvent )
#### Parameters

 _ppiLSCEvent_
  
A pointer to an ILSCEvent interface.
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_FAIL  <br/> |There are no more events.  <br/> |
|S_OK  <br/> |The call was successful.  <br/> |
   
#### IEnumLSCEvent::Reset

Resets the enumerator to the first event.
  
HRESULT IEnumLSCEvent::Reset ( )
#### Parameters

None.
  
#### Return values

Always returns S_OK. 
  
### Interface ILSCEvent

This interface represents a synchronizing event. All information about the event can be retrieved from the interface.
  
#### Public Member Functions

#### ILSCEvent::GetConflictStatus

Note that this value is populated when [ILSCLocalSyncClient::GetChanges ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_GetChanges) is called, not when the event was created, so you will only have the current status of the file, not the status of the file when the conflict status changed. 
  
This value is only populated when the [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) of the event is LSCEventType_OnLocalConflictStateChanged. 
  
HRESULT ILSCEvent::GetConflictStatus ( [out] VARIANT_BOOL \* pfIsInConflict )
#### Parameters

 _pfIsInConflict_
  
The current conflict status of the file associated with the event.
  
#### Return values

Always returns S_OK. 
  
#### ILSCEvent::GetError

This value is only populated when the [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) of the event is LSCEventType_OnServerChangesDownloaded or LSCEventType_OnLocalChangesUploaded. 
  
HRESULT ILSCEvent::GetError ( [out] LONG \* pnError )
#### Parameters

 _pnError_
  
The error associated with this event.
  
#### Return values

Always returns S_OK. 
  
#### ILSCEvent::GetETag

This value is only populated when the [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) of the event is LSCEventType_OnServerChangesDownloaded or LSCEventType_OnLocalChangesUploaded. 
  
HRESULT ILSCEvent::GetETag ( [out] BSTR \* pbstrETag )
#### Parameters

 _pbstrETag_
  
The ETag associated with this event
  
#### Return values

Always returns S_OK. 
  
#### ILSCEvent::GetEventType

Gets the type for this event.
  
HRESULT ILSCEvent::GetEventType ( [out] LSCEventType \* pnEventType )
#### Parameters

 _pnEventType_
  
The event type of this event. See [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) for valid values. Must not be null. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|S_OK  <br/> |The call was successful.  <br/> |
   
#### ILSCEvent::GetLocalWorkingPath

Gets the local working path for this event.
  
HRESULT ILSCEvent::GetLocalWorkingPath ( [out] BSTR \* pbstrLocalWorkingPath )
#### Parameters

 _pbstrLocalWorkingPath_
  
The local path of the file to which this event pertains. 
  
#### Return values

Always returns S_OK. 
  
#### ILSCEvent::GetResourceID

Gets the resource ID for the event.
  
HRESULT ILSCEvent::GetResourceID ( [out] BSTR \* pbstrResourceID )
#### Parameters

 _pbstrResourceID_
  
The ResourceID of the file associated with this event.
  
#### Return values

Always returns S_OK. 
  
#### ILSCEvent::GetResourceIDAttempted

This value is only populated when the [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) of the event is LSCEventType_OnFilePathConflict. When a call to [ILSCLocalSyncClient::LocalFileChange ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_LocalFileChange), [ILSCLocalSyncClient::ServerFileChange ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_ServerFileChange), or [ILSCLocalSyncClient::RenameFile ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_RenameFile) would cause a Web Path or Local Path collision with another file in the Office file cache, this event is generated. 
  
HRESULT ILSCEvent::GetResourceIDAttempted ( [out] BSTR \* pbstrResourceIDAttempted )
#### Parameters

 _pbstrResourceIDAttempted_
  
The ResourceID that caused this event to get generated. Must not be null. 
  
#### Return values

Always returns S_OK. 
  
#### ILSCEvent::GetSyncErrorType

This value is only populated when the [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) of the event is LSCEventType_OnServerChangesDownloaded or LSCEventType_OnLocalChangesUploaded. 
  
HRESULT ILSCEvent::GetSyncErrorType ( [out] LSCEventSyncErrorType \* pnSyncErrorType )
#### Parameters

 _pnSyncErrorType_
  
The error type associated with this event. See [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) for potential values. Must not be null. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_INVALIDARG  <br/> |One or more parameters are invalid.  <br/> |
|S_OK  <br/> |The call was successful.  <br/> |
   
#### ILSCEvent::GetWebPath

This value is only populated when the [Enum LSCEventType](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventType) of the event is LSCEventType_OnFilePathConflict. 
  
HRESULT ILSCEvent::GetWebPath ( [out] BSTR \* pbstrWebPath )
#### Parameters

 _pbstrWebPath_
  
Specifies the Web Path associated with this event. Must not be null. 
  
#### Return values

Always returns S_OK. 
  
### Interface ILSCEvent2

This interface holds additional information about a synchronizing event.
  
#### Public Member Functions

#### ILSCEvent2::GetErrorChain

Gets the error chain information about a synchronizing event.
  
HRESULT ILSCEvent2::GetErrorChain ( [out] BSTR \* pbstrErrorChain )
#### Parameters

 _pbstrErrorChain_
  
A string to hold the error chain information. Must not be null. 
  
#### Return values

|
|
|**Value**|**Description**|
|:-----|:-----|
|E_NOTIMPL  <br/> |The installed version of Office does not support this interface  <br/> |
|E_INVALIDARG  <br/> |One or more of the parameter values are invalid.  <br/> |
|E_FAIL  <br/> |The error chain information is not available.  <br/> |
|S_OK  <br/> |The call was successful.  <br/> |
   
### Interface IPartnerActivityCallback

This interface provides a callback function to the CSISyncClient COM object.
  
#### Public Member Functions

#### IPartnerActivityCallback::EventOccurred

This is a callback function on the object given to the CsiSyncClient COM object. It's expected that when an Event occurs (see [Enum LSCEventTypeOccurred](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventTypeOccurred) for valid event types), the CsiSyncClient COM object will call this method, signalling the consumer. 
  
HRESULT IPartnerActivityCallback::EventOccurred ( [in] LSCEventTypeOccurred eEventTypeOccurred )
#### Parameters

 _eEventTypeOccurred_
  
The event type of this event. See [Enum LSCEventTypeOccurred](using-csisyncclient-to-control-the-office-document-cache-odc.md#Enum_LSCEventTypeOccurred) for valid values. 
  
#### Return values

Always returns S_OK.
  
## Enumerations

CSISyncClient uses the following enumerations.
  
### Enum LSCEventSyncErrorType
<a name="Enum_LSCEventSyncErrorType"> </a>

This enumeration specifies the categories of errors that can occur while synchronizing a file.
  
|
|
|**Enumerator**|**Description**|
|:-----|:-----|
|LSCEventSyncErrorType_UserInterventionRequiredUnexpected  <br/> |The synchronizing error of this event was unexpected, and may require special consideration. By default, the user may have to intervene.  <br/> |
|LSCEventSyncErrorType_NoInterventionRequired  <br/> |The synchronizing error of this event does not need special consideration. Office will handle it automatically.  <br/> |
|LSCEventSyncErrorType_UserInterventionRequired  <br/> |The synchronizing error of this event requires a user to resolve it. For example, merge conflict error requires a user to open the document and merge it.  <br/> |
|LSCEventSyncErrorType_WaitingOnClient  <br/> |The synchronizing error of this event requires the consumer to intervene, but should not require special consideration by the user.  <br/> |
|LSCEventSyncErrorType_ClientInterventionRequired  <br/> |The synchronizing error of this event requires the consumer to intervene as a special case.  <br/> |
|LSCEventSyncErrorType_Max  <br/> ||
   
### Enum LSCEventType
<a name="Enum_LSCEventType"> </a>

This enumeration specifies the type of events that can occur for a particular file.
  
|
|
|**Enumerator**|**Description**|
|:-----|:-----|
|LSCEventType_None  <br/> ||
|LSCEventType_OnLocalChanges  <br/> |Changes were made to a local file.  <br/> |
|LSCEventType_OnOpenedByUser  <br/> |A user opened a file.  <br/> |
|LSCEventType_OnServerChangesDownloaded  <br/> |Finished downloading file changes from the server.  <br/> |
|LSCEventType_OnLocalChangesUploaded  <br/> |Finished uploading file changes to the server.  <br/> |
|LSCEventType_OnLocalConflictStateChanged  <br/> |The merge conflict state of a file has changed.  <br/> |
|LSCEventType_OnFileAdded  <br/> |A file was added.  <br/> |
|LSCEventType_OnFileDeleted  <br/> |A file was deleted.  <br/> |
|LSCEventType_OnSyncEnabled  <br/> |Synchronizing was enabled for a user's files.  <br/> |
|LSCEventType_OnServerChangesDownloadStarted  <br/> |Started downloading file changes from the server.  <br/> |
|LSCEventType_OnLocalChangesUploadStarted  <br/> |Started uploading file changes to the server.  <br/> |
|LSCEventType_OnFilePathConflict  <br/> |This event is generated when a call to [ILSCLocalSyncClient::LocalFileChange ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_LocalFileChange), [ILSCLocalSyncClient::ServerFileChange ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_ServerFileChange), or [ILSCLocalSyncClient::RenameFile ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_RenameFile) causes a Web Path or Local Path collision with another file in the Office file cache.  <br/> |
|LSCEventType_OnFileForked  <br/> ||
|LSCEventType_Max  <br/> ||
   
### Enum LSCEventTypeOccurred
<a name="Enum_LSCEventTypeOccurred"> </a>

This enumeration specifies the type of events that can occur. The consumer needs to call specific ILSCLocalSyncClient functions based on the event type.
  
|
|
|**Enumerator**|**Description**|
|:-----|:-----|
|LSCEventTypeOccurred_GetChanges  <br/> |An ILSCEvent has occurred. The consumer should call [ILSCLocalSyncClient::GetChanges ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_GetChanges) to retrieve the data.  <br/> |
|LSCEventTypeOccurred_GetSupportedFileExtensions  <br/> |The supported file extensions have changed. The consumer should call [ILSCLocalSyncClient::GetSupportedFileExtensions ](using-csisyncclient-to-control-the-office-document-cache-odc.md#ILSCLocalSyncClient_GetSupportedFileExtensions) to retrieve the new list of supported extensions.  <br/> |
   
### Enum LSCNetworkSyncPermissionType
<a name="Enum_LSCNetworkSyncPermissionType"> </a>

This enumeration specifies the flags used for a network cost heuristic. 
  
|
|
|**Enumerator**|**Description**|
|:-----|:-----|
|LSCNetworkSyncPermissionType_HighCost  <br/> |True if the cost heuristic for expensive networks (such as 3G) is overridden.  <br/> |
|LSCNetworkSyncPermissionType_HighPowerUsage  <br/> |True if the cost heuristic for power usage (such as a battery) is overridden.  <br/> |
   
### Enum LSCStatusFlag
<a name="Enum_LSCStatusFlag"> </a>

This enumeration is used to represent the synchronize status of a file. 
  
|
|
|**Enumerator**|**Description**|
|:-----|:-----|
|LCSStatusFlag_None  <br/> ||
|LSCStatusFlag_UploadPending  <br/> |True if there is pending data to send to the server file.  <br/> |
|LSCStatusFlag_DownloadPending  <br/> |True if there is pending data to download from the server file.  <br/> |
|LSCStatusFlag_LocalFileUnchanged  <br/> |True if the data Office has on the file in its cache is the most recent copy of the data on disk.  <br/> |
   

