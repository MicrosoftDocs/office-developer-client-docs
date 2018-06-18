---
title: "Optional Features for Address Book Providers"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: f1558259-7f0b-4731-80d2-88e51e203df0
description: "Last modified: March 09, 2015"
 
 
---

# Optional Features for Address Book Providers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
There are many optional features for address book providers. Some of the more commonly implemented features include:
  
- Acting as a foreign provider by allowing entries from one of your containers to be added to another provider's container.
    
- Acting as a host provider by adding entries from another provider to one of your containers.
    
- Advanced searching.
    
- Prefix scrolling through contents tables.
    
- Support for distribution lists.
    
- Support for event notification.
    
The following table briefly describes these optional features and how you implement them:
  
|**Feature**|**How to implement**|
|:-----|:-----|
|Supply templates for creating entries for message recipient lists  <br/> |Implement the [IABLogon::GetOneOffTable](iablogon-getoneofftable.md) method. For more information, see [One-Off Tables](one-off-tables.md) and [Implementing One-Off Tables](implementing-one-off-tables.md).  <br/> |
|Group recipients into a named unit  <br/> |Support the properties of distribution lists by implementing the [IDistList : IMAPIContainer](idistlistimapicontainer.md) interface.  <br/> |
|Act as a foreign address book provider by allowing entries to be added to a container in another provider  <br/> | Support binding code to data in the host provider by:  <br/>  Supporting the **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property on messaging users and distribution lists. For more information, see [Address Book Identifiers](address-book-identifiers.md).  <br/>  Implementing the [IABLogon::OpenTemplateID](iablogon-opentemplateid.md) method. For more information, see [Acting as a Foreign Address Book Provider](acting-as-a-foreign-address-book-provider.md).  <br/> |
|Acting as a host address book provider by inserting entries from another provider  <br/> |Support binding data to code from a foreign provider by calling the [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md) method. For more information, see [Acting as a Host Address Book Provider](acting-as-a-host-address-book-provider.md).  <br/> |
|Prefix scrolling  <br/> |Support restrictions on container contents tables. For more information, see [About Restrictions](about-restrictions.md).  <br/> |
|Advanced searching in a container  <br/> |Support the **PR_SEARCH** ([PidTagSearch](pidtagsearch-canonical-property.md)) property on containers. For more information, see [Implementing Advanced Searching](implementing-advanced-searching.md).  <br/> |
|Event notification  <br/> |Implement the [IABLogon::Advise](iablogon-advise.md) and [IABLogon::Unadvise](iablogon-unadvise.md) methods. For more information, see [Event Notification in MAPI](event-notification-in-mapi.md) and [Supporting Event Notification](supporting-event-notification.md).  <br/> |
   
For event notification, your **IABLogon::Advise** method will be called by MAPI when a client calls **IAddrBook::Advise** to register for notifications on any one of your containers, messaging users, or distribution lists. However, because supporting event notification is optional, you can return MAPI_E_NO_SUPPORT from these methods. However, MAPI does recommend that you at least support notifications on your contents tables and encourages you to support all types of object notification except for  _fnevSearchComplete_ and the  _fnevCriticalError_ event to add value. 
  

