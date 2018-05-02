---
title: "Required Features for Address Book Providers"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e2ccddd7-65e8-41f6-8e21-a4ae98190a96
description: "Last modified: March 09, 2015"
 
 
---

# Required Features for Address Book Providers

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Address book providers can work with recipient information that is temporary or permanent, local or remote, understandable by one or more messaging systems, and formatted for a disk file or database table. There are a variety of features that an address book provider can implement, thereby adding value and improving interoperability with clients and other providers. However, a few features are required.
  
The following table describes features that are required of all address book providers and the steps that you need to take to implement them.
  
|**Feature**|**How to implement**|
|:-----|:-----|
|Session logon  <br/> | Implement an entry point function. For more information, see [Implementing an Address Book Provider Entry Point Function](implementing-an-address-book-provider-entry-point-function.md).  <br/>  Implement the [IABProvider::Logon](iabprovider-logon.md) method. For more information, see [Implementing Address Book Provider Logon and Logoff](implementing-address-book-provider-logon-and-logoff.md).  <br/> |
|Session logoff  <br/> |Implement the [IABProvider::Shutdown](iabprovider-shutdown.md) method. For more information, see [Implementing Address Book Provider Logon and Logoff](implementing-address-book-provider-logon-and-logoff.md).  <br/> |
|Create entry identifiers  <br/> |Provide support for the **PR_ENTRYID** ( [PidTagEntryId](pidtagentryid-canonical-property.md)) property. For more information, see [MAPI Entry Identifiers](mapi-entry-identifiers.md) and [Address Book Identifiers](address-book-identifiers.md).  <br/> |
|Contribute to the status table  <br/> | Implement the appropriate methods of the [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md) interface. For more information, see [Status Object Implementation](status-object-implementation.md).  <br/>  Support the required status table properties. For more information, see [Status Tables](status-tables.md).  <br/>  Call [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md).  <br/> |
|Provide limited status object support  <br/> | Implement the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method.  <br/>  Return MAPI_E_NO_SUPPORT from the other **IMAPIStatus** methods.  <br/> |
|Support interactive and programmatic configuration  <br/> | Implement a message service entry point function.  <br/>  Implement a display table. For more information, see [Display Tables](display-tables.md) and [Display Table Implementation](display-table-implementation.md).  <br/>  Implement a property sheet or call the [IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md) method. For more information, see [Property Sheet Implementation](property-sheet-implementation.md).  <br/> |
   
In addition, if your provider supports recipient creation, you must supply a list of creation templates. Supply this list by implementing the [IABLogon::GetOneOffTable](iablogon-getoneofftable.md) method to include all of the templates supported by your provider and the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method of each container to open the **PR_CREATE_TEMPLATES** ( [PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property and include all the templates supported by the container. For more information, see [Implementing One-Off Tables](implementing-one-off-tables.md).
  

