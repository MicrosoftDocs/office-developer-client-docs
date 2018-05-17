---
title: "Status Object Implementation"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 48fd3e28-c2d2-474d-9487-5e2f08ca7319
description: "Last modified: July 23, 2011"
 
 
---

# Status Object Implementation

  
  
**Applies to**: Outlook 
  
All service providers must implement a status object and furnish properties from it to the session status table. You can include one or more rows in the status table, depending on the number of resources that you control. A transport provider, for example, should create a row in the status table for each message queue it manages. When changes occur, the appropriate status table row must be updated. Status objects are implemented to provide access both to the information included in the status table and to additional information not included in the table.
  
## To implement a status object

1. Implement the **OpenStatusEntry** method of your logon object. When clients want to open your status object, they call [IMAPISession::OpenEntry](imapisession-openentry.md). MAPI fulfills the open request by calling your provider's **OpenStatusEntry** method, causing your provider to open its status object and return to the client a pointer to its **IMAPIStatus** implementation. In your **OpenStatusEntry** implementation, complete the following steps: 
    
1. Perform the following tasks if your logon object has not yet created a status object:
    
1. Call the support object's [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) method to access your provider's profile section. 
    
2. Create a new status object.
    
3. Store a reference to the profile section in your provider's status object and call the profile section's [IUnknown::AddRef](http://msdn.microsoft.com/library/b4316efd-73d4-4995-b898-8025a316ba63%28Office.15%29.aspx) method to increment its reference count. 
    
4. Store a reference to the logon object in your provider's status object and call the logon object's **IUnknown::AddRef** method to increment its reference count. 
    
5. Store a reference to the status object in your provider's logon object.
    
2. Call the status object's **IUnknown::AddRef** method to increment its reference count in the logon object. 
    
3. Set the status object's **PR_OBJECT_TYPE** ( [PidTagObjectType](pidtagobjecttype-canonical-property.md)) property to MAPI_STATUS.
    
4. Set the  _lppMAPIStatus_ output parameter to point to the status object, and return. 
    
5. Check the  _ulFlags_ input parameter. If it is set to MAPI_MODIFY and your provider supports read/write access to its status object, return a writeable object. However, if your provider does not support read/write access to its status object, do not fail. Return a status object that is read-only. Clients that expect to receive read/write status objects should verify that read/write permission has been granted before attempting to make any changes. 
    
2. Set all of the required status object and status table properties. The properties that you include in your status table row should be available through your status object, except for the properties calculated by MAPI. The required properties are as follows:
    
  - **PR_DISPLAY_NAME** ( [PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
  - **PR_PROVIDER_DLL_NAME** ( [PidTagProviderDllName](pidtagproviderdllname-canonical-property.md))
    
  - **PR_PROVIDER_DISPLAY** ( [PidTagProviderDisplay](pidtagproviderdisplay-canonical-property.md))
    
  - **PR_RESOURCE_TYPE** ( [PidTagResourceType](pidtagresourcetype-canonical-property.md))
    
  - **PR_RESOURCE_METHODS** ( [PidTagResourceMethods](pidtagresourcemethods-canonical-property.md))
    
  - **PR_RESOURCE_FLAGS** ( [PidTagResourceFlags](pidtagresourceflags-canonical-property.md))
    
  - **PR_STATUS_CODE** ( [PidTagStatusCode](pidtagstatuscode-canonical-property.md))
    
3. Implement the [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) methods that are appropriate for your provider. Depending on your provider, you do not need to implement all of the four methods in **IMAPIStatus**. Every provider should implement a read-only version of the methods of the [IMAPIProp : IUnknown](imapipropiunknown.md) interface and the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method. Transport providers should also implement [IMAPIStatus::FlushQueues](imapistatus-flushqueues.md), and all providers should support [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md). However, support for [IMAPIStatus::ChangePassword](imapistatus-changepassword.md) is optional. Only service providers that require passwords and want to allow users to change them programmatically need to implement this method. For every method that you support, set the corresponding bit in the **PR_RESOURCE_METHODS** property. For example, if you support **ValidateState** and **SettingsDialog** only, set **PR_RESOURCE_METHODS** to the following: 
    
     `STATUS_VALIDATE_STATE | STATUS_SETTINGS_DIALOG`
    
    Clients should check the value of **PR_RESOURCE_METHODS** before attempting to call your status object. Handle calls to any of your unsupported methods by returning MAPI_E_NO_SUPPORT. 
    
4. Call [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) during logon to add your row or rows to the status table. Pass a property value array that contains the column information for the row and 0 for the  _ulFlags_ parameter. If at some point later in the session your provider's status changes and it becomes necessary to update the column information, call **ModifyStatusRow** again with the STATUSROW_UPDATE flag set. 
    
For more information about status objects, see [MAPI Status Objects](mapi-status-objects.md).
  
## See also

#### Concepts

[MAPI Service Providers](mapi-service-providers.md)

