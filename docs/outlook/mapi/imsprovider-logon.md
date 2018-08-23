---
title: "IMSProviderLogon"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMSProvider.Logon
api_type:
- COM
ms.assetid: 890d9cbe-3570-4cf0-aeae-667c0e5ba181
description: "Last modified: July 23, 2011"
---

# IMSProvider::Logon

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Logs MAPI on to one instance of a message store provider.
  
```cpp
HRESULT Logon(
  LPMAPISUP lpMAPISup,
  ULONG_PTR ulUIParam,
  LPSTR lpszProfileName,
  ULONG cbEntryID,
  LPENTRYID lpEntryID,
  ULONG ulFlags,
  LPCIID lpInterface,
  ULONG FAR * lpcbSpoolSecurity,
  LPBYTE FAR * lppbSpoolSecurity,
  LPMAPIERROR FAR * lppMAPIError,
  LPMSLOGON FAR * lppMSLogon,
  LPMDB FAR * lppMDB
);
```

## Parameters

 _lpMAPISup_
  
> [in] A pointer to the current MAPI support object for the message store.
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows this method displays. 
    
 _lpszProfileName_
  
> [in] A pointer to a string that contains the name of the profile being used for store provider logon. This string can be displayed in dialog boxes, written out to a log file, or simply ignored. It must be in Unicode format if the MAPI_UNICODE flag is set in the  _ulFlags_ parameter. 
    
 _cbEntryID_
  
> [in] The size, in bytes, of the entry identifier pointed to by the  _lpEntryID_ parameter. 
    
 _lpEntryID_
  
> [in] A pointer to the entry identifier for the message store. Passing **null** in  _lpEntryID_ indicates that a message store has not yet been selected and that dialog boxes that enable the user to select a message store can be presented. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the logon is performed. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> The call is allowed to succeed even if the underlying object is not available to the calling implementation. If the object is not available, a subsequent call to the object might raise an error.
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If MAPI_UNICODE is not set, the strings are in ANSI format.
    
MDB_NO_DIALOG 
  
> Prevents the display of logon dialog boxes. If this flag is set, the error value MAPI_E_LOGON_FAILED is returned if the logon is unsuccessful. If this flag is not set, the message store provider can prompt the user to correct a name or password, to insert a disk, or to perform other actions that are necessary to establish connection to the store.
    
MDB_NO_MAIL 
  
> The message store should not be used for sending or receiving mail. The flag signals MAPI not to notify the MAPI spooler that this message store is being opened. If this flag is set and the message store is tightly coupled with a transport provider, the provider does not need to call the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method. 
    
MDB_TEMPORARY 
  
> Logs on the store so that information can be retrieved programmatically from the profile section, without use of dialog boxes. This flag instructs MAPI that the store is not to be added to the message store table and that the store cannot be made permanent. If this flag is set, message store providers do not need to call the [IMAPISupport::ModifyProfile](imapisupport-modifyprofile.md) method. 
    
MDB_WRITE 
  
> Requests read/write permission.
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) for the message store to log on to. Passing **null** indicates the MAPI interface for the message store ( [IMsgStore](imsgstoreimapiprop.md)) is returned. The  _lpInterface_ parameter can also be set to an identifier for an appropriate interface for the message store (for example, IID_IUnknown or IID_IMAPIProp). 
    
 _lpcbSpoolSecurity_
  
> [out] A pointer to the variable in which the store provider returns the size, in bytes, of the validation data in the  _lppbSpoolSecurity_ parameter. 
    
 _lppbSpoolSecurity_
  
> [out] A pointer to the pointer to the returned validation data. This validation data is provided so the [IMSProvider::SpoolerLogon](imsprovider-spoolerlogon.md) method can log the MAPI spooler on to the same store as the message store provider. 
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to the returned [MAPIERROR](mapierror.md) structure, if any, that contains version, component, and context information for an error. The  _lppMAPIError_ parameter can be set to **null** if there is no **MAPIERROR** structure to return. 
    
 _lppMSLogon_
  
> [out] A pointer to the pointer to the message store logon object for MAPI to log on to.
    
 _lppMDB_
  
> [out] A pointer to the pointer to the message store object for the MAPI spooler and client applications to log on to.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_FAILONEPROVIDER 
  
> This provider cannot log on, but this error should not disable the service. 
    
MAPI_E_LOGON_FAILED 
  
> A logon session could not be established.
    
MAPI_E_UNCONFIGURED 
  
> The profile does not contain enough information for the logon to complete. When this value is returned, MAPI calls the message store provider's message-service entry point function.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
MAPI_E_UNKNOWN_CPID 
  
> The server is not configured to support the client's code page.
    
MAPI_E_UNKNOWN_LCID 
  
> The server is not configured to support the client's locale information.
    
MAPI_W_ERRORS_RETURNED 
  
> The call succeeded, but the message store provider has error information available. When this warning is returned, the call should be handled as successful. To test for this warning, use the **HR_FAILED** macro. For more information, see [Using Macros for Error Handling](using-macros-for-error-handling.md). To get the error information from the provider, call the [IMAPISession::GetLastError](imapisession-getlasterror.md) method. 
    
## Remarks

MAPI calls the **IMSProvider::Logon** method to do the majority of processing necessary to obtain access to a message store. Message store providers validate any user credentials necessary to access a particular store and return a message store object in the  _lppMDB_ parameter that the MAPI spooler and client applications can log on to. 
  
In addition to the returned message store object for client and MAPI spooler use, the provider also returns a message store logon object for MAPI to use in controlling the opened store. The message store logon object and the message store object should be tightly linked inside the message store provider so each can affect the other. The use of the store object and the logon object should be identical; there should be a one-to-one correspondence between the logon object and the store object such that the objects act as if they are one object that exposes two interfaces. The two objects should also be created together and freed together. 
  
The MAPI support object, created by MAPI and passed to the provider in the  _lpMAPISup_ parameter, provides access to functions in MAPI that the provider requires. These include functions that save and retrieve profile information, access address books, and so on. The  _lpMAPISup_ pointer can be different for each store that is opened. While processing calls for a message store after logon, the store provider should use the  _lpMAPISup_ variable that is specific to that store. For any **Logon** call that opens a message store and succeeds in creating a message store logon object, the provider must save a pointer to the MAPI support object in the store logon object and must call the [IUnknown::AddRef](http://msdn.microsoft.com/en-us/library/ms691379%28v=VS.85%29.aspx) method to add a reference for the support object. 
  
The  _ulUIParam_ parameter should be used if the provider presents dialog boxes during the **Logon** call. However, dialog boxes should not be presented if  _ulFlags_ contains the MDB_NO_DIALOG flag. If a user interface needs to be called but  _ulFlags_ does not allow it, or if for some other reason a user interface cannot be displayed, the provider should return MAPI_E_LOGON_FAILED. If **Logon** displays a dialog box and the user cancels the logon, typically by clicking the dialog box's **Cancel** button, the provider should return MAPI_E_USER_CANCEL. 
  
The  _lpEntryID_ parameter can either be **null** or point to an unwrapped store entry identifier that this message store previously created. If  _lpEntryID_ points to an unwrapped entry identifier, that entry identifier can come from one of several places: 
  
- It can be an entry identifier that the store provider previously wrapped and wrote to the profile section as a **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property.
    
- It can be an entry identifier that the provider previously wrapped and returned to a calling client as a **PR_STORE_ENTRYID** ([PidTagStoreEntryId](pidtagstoreentryid-canonical-property.md)) property. 
    
- It can be an entry identifier that the provider previously wrapped and returned to a calling client as the **PR_ENTRYID** property of a message store object. 
    
In any of these cases, it is possible that the entry identifier was created on a different computer than the one currently being used.
  
When  _lpEntryID_ is not **null**, it should contain all of the information needed to identify and locate the message store. This information can include network volume names, phone numbers, user account names, and so on. If the connection to the store cannot be made by using the data in the entry identifier, the store provider should display a dialog box that enables the user to select the store to be opened. A dialog box might be required, for example, if a server has been renamed, an account name has changed, or portions of the network are not available.
  
When  _lpEntryID_ is **null**, the message store to use has not yet been selected. The provider can still access a store without displaying a dialog box if it supports further methods to specify the store. For example, the provider can check its initialization file, or it can look for additional properties that were placed in its or its message service's profile section at configuration.
  
If a provider finds that all the required information is not in the profile, it should return MAPI_E_UNCONFIGURED. MAPI will then call the provider's message service entry point function to enable the user to select a store, or even to create one, and to enter an account name and password, as needed. MAPI automatically creates a new profile section for a new store; this new profile section can be temporary or permanent, depending on how it has been added. If the store provider calls the **IMAPISupport::ModifyProfile** method, the new profile section becomes permanent and the store is added to the list of message stores returned by the [IMAPISession::GetMsgStoresTable](imapisession-getmsgstorestable.md) method. 
  
The  _lpInterface_ parameter specifies the IID of the interface required for the newly opened store object. Passing **null** in  _lpInterface_ specifies that the MAPI message store interface, **IMsgStore**, is required. Passing the message store object, IID_IMsgStore, also specifies that **IMsgStore** is required. If IID_IUnknown is passed in  _lpInterface_, the provider should open the store by using whatever interface derived from [IUnknown](http://msdn.microsoft.com/en-us/library/ms680509%28v=VS.85%29.aspx) is best for the provider (again, this is typically **IMsgStore**). When IID_IUnknown is passed, the calling implementation uses the [IUnknown::QueryInterface](http://msdn.microsoft.com/en-us/library/ms682521%28v=VS.85%29.aspx) method to select an interface after the store open operation succeeds. 
  
The **IMSProvider::Logon** call should return sufficient information, such as a path to the store and credentials for accessing the store, to allow the MAPI spooler to log on to the same store that the store provider does without presenting a dialog box. The  _lpcbSpoolSecurity_ and  _lppbSpoolSecurity_ parameters are used to return this information. The provider allocates the memory for this data by passing a pointer to a buffer in the [MSProviderInit](msproviderinit.md) function's  _lpfAllocateBuffer_ parameter; the provider places the size of this buffer in  _lpcbSpoolSecurity_. 
  
MAPI frees this buffer when appropriate. If the MAPI spooler's logon to the store can be accomplished from the information in the profile section alone, the provider can return null in  _lppbSpoolSecurity_ and 0 for the information's size in  _lpcbSpoolSecurity_. The MAPI spooler logon occurs as part of a different process than the store logon; because the buffer that contains the passed information gets copied between processes, it might not be in memory at the same location for the MAPI spooler process as for the store provider process. Therefore, a provider shouldn't put addresses into this buffer. For more information about MAPI spooler logon, see the [IMSProvider::SpoolerLogon](imsprovider-spoolerlogon.md) method. 
  
Most store providers use the [IMAPISession::OpenProfileSection](imapisession-openprofilesection.md) method of the support object passed in the  _lpMAPISup_ parameter for saving and retrieving user credentials and options. **OpenProfileSection** enables a store provider to save additional arbitrary information in a profile section and associate it with a particular resource. For example, a store provider can save the user account name and password associated with a resource and any paths or other information needed to access that resource. 
  
Properties with property identifiers 0x6600 through 0x67FF are secure properties available to the provider for its own use to store private data in profile sections. For more information about the uses of properties in profile section objects, see the [IProfSect : IMAPIProp](iprofsectimapiprop.md) method. 
  
In addition to any private data in properties with identifiers 0x6600 through 0x67FF, the store provider should provide information for the **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property in its profile section. It should put in **PR_DISPLAY_NAME** the display name of the provider itself — an identifying string (for example, "Microsoft Personal Information Store") that is displayed to users so they can distinguish this message store from others they might have access to. **PR_DISPLAY_NAME** commonly contains a server name, user account name, or path. 
  
Some profile section properties are visible in the message store table; others are visible during setup, installation, and configuration of the MAPI subsystem. The provider typically provides information for these visible properties both for a new profile section, which does not yet include saved credentials or private information, and when it finds that property information has changed. For more information about profile sections, see [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md).
  
After successfully logging on a user, and before returning to MAPI, the store provider should create the array of properties for the status row for the resource and call the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method. 
  
 **Logon** calls that open message stores that are already open for the current MAPI session skip much of the processing previously described. These calls do not create status rows, return message store logon objects, call **AddRef** for the MAPI support object, or return data for MAPI spooler logon. These calls do return S_OK and return a message store object with the requested interface. 
  
To detect such calls, the provider should maintain a list in the message store provider object of stores already open for this provider object. When processing a **Logon** call, the provider should scan this list of open stores and determine whether the store to be logged on to is already open. If it is, user credentials do not need to be checked and the display of a dialog box should be avoided, if possible. If dialog boxes must be displayed, the provider should check returned information to see whether a store has been opened a second time. In addition, the provider should check for duplicate openings by using  _lpEntryID_ at the beginning of **Logon** call processing. 
  
Standard processing for a **Logon** call that accesses an open store is as follows: 
  
1. The store provider calls **AddRef** for the existing store object if the new interface being requested is the same as the interface for the existing store. Otherwise, it calls **QueryInterface** to get the new interface. If the store does not support the new interface, the provider should return the error value MAPI_E_INTERFACE_NOT_SUPPORTED. 
    
2. The provider returns a pointer to the required interface of the existing store object in  _lppMDB_.
    
3. The provider returns **null** in  _lppMSLogon_.
    
4. The provider should not open the profile for the support object passed in the call. In addition, it should not register a provider unique identifier, register a status row, or return MAPI spooler logon data.
    
5. The provider should not call **AddRef** for the support object, because it does not require a pointer to the object. 
    
Whenever possible, providers should return appropriate error and warning strings for **Logon** calls, because doing so greatly eases the burden of users in determining why something did not work. To return these strings, a provider sets the members in the **MAPIERROR** structure. MAPI looks for, uses, and releases the **MAPIERROR** structure if it is returned by a provider. 
  
Memory for this **MAPIERROR** structure should be allocated by using the buffer passed in  _lpfAllocateBuffer_ on the **MSProviderInit** call. Any error strings contained in the returned structure should be in Unicode format if MAPI_UNICODE is set in the **Logon** _ulFlags;_ otherwise, they should be in the ANSI character set. 
  
For most error values returned from **Logon**, MAPI disables the message services to which the failing provider belongs. MAPI will not call any providers that belong to those services for the life of the MAPI session. In contrast, when **Logon** returns the MAPI_E_FAILONEPROVIDER error value from its logon, MAPI does not disable the message service to which the provider belongs. **Logon** should return MAPI_E_FAILONEPROVIDER if it encounters an error that does not warrant disabling the entire service for the life of the session. For example, a provider might return this error when it does not allow the display of a user interface and a required password is unavailable. 
  
If a provider returns MAPI_E_UNCONFIGURED from its logon, MAPI will call the provider's message service entry function and then retry the logon. MAPI passes MSG_SERVICE_CONFIGURE as the context to give the service a chance to configure itself. If the client has chosen to allow a user interface on the logon, the service can present its configuration property sheet so the user can enter configuration information.
  
## See also



[IMAPISession::GetMsgStoresTable](imapisession-getmsgstorestable.md)
  
[IMAPISession::OpenMsgStore](imapisession-openmsgstore.md)
  
[IMAPISession::OpenProfileSection](imapisession-openprofilesection.md)
  
[IMAPISupport::ModifyProfile](imapisupport-modifyprofile.md)
  
[IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md)
  
[IMsgStore : IMAPIProp](imsgstoreimapiprop.md)
  
[IMSProvider::SpoolerLogon](imsprovider-spoolerlogon.md)
  
[IProfSect : IMAPIProp](iprofsectimapiprop.md)
  
[MAPIERROR](mapierror.md)
  
[MSProviderInit](msproviderinit.md)
  
[IMSProvider : IUnknown](imsprovideriunknown.md)

