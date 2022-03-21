---
title: "IMAPISupport  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport
api_type:
- COM
ms.assetid: 92bfe604-18dd-46a1-9ae8-0b04167606bd
description: "Last modified: March 09, 2015"
---

# IMAPISupport : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Provides implementations for tasks that are typically performed by service providers and message service entry point functions. Service providers receive a pointer to their support object when MAPI calls their provider object's logon method. Message services receive their support object pointer in the call to their entry point function.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Exposed by:  <br/> |Support objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Service providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPISup  <br/> |
|Pointer type:  <br/> |LPMAPISUP  <br/> |
   
## Vtable order

|Member |Description|
|:-----|:-----|
|[GetLastError](imapisupport-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous support object error. |
|[GetMemAllocRoutines](imapisupport-getmemallocroutines.md) <br/> |Retrieves the addresses of the MAPI memory allocation and deallocation functions ([MAPIAllocateBuffer](mapiallocatebuffer.md), [MAPIAllocateMore](mapiallocatemore.md), and [MAPIFreeBuffer](mapifreebuffer.md)). |
|[Subscribe](imapisupport-subscribe.md) <br/> |Registers an advise sink to receive notifications through MAPI. |
|[Unsubscribe](imapisupport-unsubscribe.md) <br/> |Cancels the responsibility for sending notifications that was previously established with a call to the **Subscribe** method. |
|[Notify](imapisupport-notify.md) <br/> |Sends a notification of a specified event to an advise source that originally registered for the notification through the **Subscribe** method. |
|[ModifyStatusRow](imapisupport-modifystatusrow.md) <br/> |Modifies the status table by adding a new row or modifying an existing row. |
|[OpenProfileSection](imapisupport-openprofilesection.md) <br/> |Opens a section of the current profile and returns an [IProfSect](iprofsectimapiprop.md) pointer for further access  <br/> |
|[RegisterPreprocessor](imapisupport-registerpreprocessor.md) <br/> |Registers a transport provider's preprocessor function (a function that conforms to the [PreprocessMessage](preprocessmessage.md) prototype). |
|[NewUID](imapisupport-newuid.md) <br/> |Creates a new [MAPIUID](mapiuid.md) structure to be used as a unique identifier. |
|[MakeInvalid](imapisupport-makeinvalid.md) <br/> |Marks an object as unusable. |
|[SpoolerYield](imapisupport-spooleryield.md) <br/> |Gives control of the CPU to the MAPI spooler so that it can perform any tasks it considers necessary. |
|[SpoolerNotify](imapisupport-spoolernotify.md) <br/> |Notifies the MAPI spooler of a change in status or a request for service. |
|[CreateOneOff](imapisupport-createoneoff.md) <br/> |Creates an entry identifier for a one-off address. |
|[SetProviderUID](imapisupport-setprovideruid.md) <br/> |Registers a **MAPIUID** structure that uniquely represents the service provider. |
|[CompareEntryIDs](imapisupport-compareentryids.md) <br/> |Compares two entry identifiers to determine whether they refer to the same object. |
|[OpenTemplateID](imapisupport-opentemplateid.md) <br/> |Opens a recipient entry in a foreign address book provider. |
|[OpenEntry](imapisupport-openentry.md) <br/> |Opens an object and returns an interface pointer for further access. |
|[GetOneOffTable](imapisupport-getoneofftable.md) <br/> |Returns a pointer to the MAPI one-off table (a list of templates that all address book providers support for creating new recipients). |
|[Address](imapisupport-address.md) <br/> |Displays the common address dialog box. |
|[Details](imapisupport-details.md) <br/> |Displays a dialog box that shows details about a particular address book entry. |
|[NewEntry](imapisupport-newentry.md) <br/> |Adds a new recipient directly to an address book container or to the recipient list of an outgoing message. |
|[DoConfigPropsheet](imapisupport-doconfigpropsheet.md) <br/> |Displays a configuration property sheet. |
|[CopyMessages](imapisupport-copymessages.md) <br/> |Copies or moves messages from one folder to another folder. |
|[CopyFolder](imapisupport-copyfolder.md) <br/> |Copies or moves a folder from its current parent folder to another parent folder. |
|[DoCopyTo](imapisupport-docopyto.md) <br/> |Copies or moves all properties of one object, except for specifically excluded properties, to another object. |
|[DoCopyProps](imapisupport-docopyprops.md) <br/> |Copies or moves one or more properties of an object to another object. |
|[DoProgressDialog](imapisupport-doprogressdialog.md) <br/> |Retrieves a progress object that displays a progress indicator. |
|[ReadReceipt](imapisupport-readreceipt.md) <br/> |Generates a read or nonread report for a message. |
|[PrepareSubmit](imapisupport-preparesubmit.md) <br/> |Prepares a message for submission to the MAPI spooler. |
|[ExpandRecips](imapisupport-expandrecips.md) <br/> |Completes a message's recipient list, expanding particular distribution lists. |
|[DoSentMail](imapisupport-dosentmail.md) <br/> |Processes a sent message. |
|[OpenAddressBook](imapisupport-openaddressbook.md) <br/> |Provides access to the address book. |
|[CompleteMsg](imapisupport-completemsg.md) <br/> |Performs postprocessing on a message. |
|[StoreLogoffTransports](imapisupport-storelogofftransports.md) <br/> |Requests the orderly release of a message store. |
|[StatusRecips](imapisupport-statusrecips.md) <br/> |Generates delivery and nondelivery reports. |
|[WrapStoreEntryID](imapisupport-wrapstoreentryid.md) <br/> |Converts a message store's internal entry identifier to an entry identifier in the MAPI standard format. |
|[ModifyProfile](imapisupport-modifyprofile.md) <br/> |Makes changes to a message store profile section permanent. |
|[IStorageFromStream](imapisupport-istoragefromstream.md) <br/> |Implements a storage object to access a stream. |
|[GetSvcConfigSupportObj](imapisupport-getsvcconfigsupportobj.md) <br/> |Creates a message service support object. |
   
## Remarks

Address books, message stores, transport providers, and message services each have their own support objects. Service providers and message services call the methods in their support objects as part of their implementations of other interface methods. Each different support object has complete implementations of the methods that apply to its caller; the methods that are not applicable return MAPI_E_NO_SUPPORT. Address book provider support objects have implementations for the following methods:
  
|Method |... |... |
|:-----|:-----|:-----|
|**Address** <br/> |**CompareEntryIDs** <br/> |**CreateOneOff** <br/> |
|**Details** <br/> |**DoConfigPropsheet** <br/> |**DoProgressDialog** <br/> |
|**GetLastError** <br/> |**GetMemAllocRoutines** <br/> |**GetOneOffTable** <br/> |
|**IStorageFromStream** <br/> |**GetSvcConfigSupportObj** <br/> |**MakeInvalid** <br/> |
|**ModifyStatusRow** <br/> |**NewEntry** <br/> |**NewUID** <br/> |
|**Notify** <br/> |**OpenAddressBook** <br/> |**OpenEntry** <br/> |
|**OpenProfileSection** <br/> |**OpenTemplateID** <br/> |**SetProviderUID** <br/> |
|**Subscribe** <br/> |**Unsubscribe** <br/> |**WrapStoreEntryID** <br/> |
   
Message store provider support objects have implementations for the following methods:
  
|Method |... |... |
|:-----|:-----|:-----|
|**CompareEntryIDs** <br/> |**CompleteMsg** <br/> |**CopyFolder** <br/> |
|**CopyMessages** <br/> |**CreateOneOff** <br/> |**DoCopyProps** <br/> |
|**DoCopyTo** <br/> |**DoConfigPropsheet** <br/> |**DoProgressDialog** <br/> |
|**DoSentMail** <br/> |**ExpandRecips** <br/> |**GetLastError** <br/> |
|**GetMemAllocRoutines** <br/> |**GetSvcConfigSupportObj** <br/> |**MakeInvalid** <br/> |
|**IStorageFromStream** <br/> |**ModifyProfile** <br/> |**ModifyStatusRow** <br/> |
|**NewUID** <br/> |**Notify** <br/> |**OpenAddressBook** <br/> |
|**OpenEntry** <br/> |**OpenProfileSection** <br/> |**PrepareSubmit** <br/> |
|**ReadReceipt** <br/> |**SetProviderUID** <br/> |**SpoolerNotify** <br/> |
|**StoreLogoffTransports** <br/> |**Subscribe** <br/> |**Unsubscribe** <br/> |
|**WrapStoreEntryID** <br/> |
   
Transport provider support objects have implementations for the following methods:
  
|Method |... |... |
|:-----|:-----|:-----|
|**DoConfigPropsheet** <br/> |**CompareEntryIDs** <br/> |**CreateOneOff** <br/> |
|**GetMemAllocRoutines** <br/> |**GetSvcConfigSupportObj** <br/> |**GetLastError** <br/> |
|**IStorageFromStream** <br/> |**MakeInvalid** <br/> |**ModifyStatusRow** <br/> |
|**OpenAddressBook** <br/> |**RegisterPreprocessor** <br/> |**NewUID** <br/> |
|**Notify** <br/> |**OpenProfileSection** <br/> |**OpenEntry** <br/> |
|**StatusRecips** <br/> |**SpoolerNotify** <br/> |**SpoolerYield** <br/> |
|**WrapStoreEntryID** <br/> |**Subscribe** <br/> |**Unsubscribe** <br/> |
   
Message service support objects have implementations for the following methods:
  
|Method |... |
|:-----|:-----|
|**DoConfigPropsheet** <br/> |**GetLastError** <br/> |
|**GetMemAllocRoutines** <br/> |**GetSvcConfigSupportObj** <br/> |
|**MakeInvalid** <br/> |**NewUID** <br/> |
|**OpenProfileSection** <br/> |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

