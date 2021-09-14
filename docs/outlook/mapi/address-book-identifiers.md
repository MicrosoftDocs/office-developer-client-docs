---
title: "Address Book Identifiers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 40f6c699-86aa-4324-a30d-12c8f1e2de9c
description: "Last modified: July 23, 2011"
 
 
---

# Address Book Identifiers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
All address book providers assign entry identifiers using the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) property to their messaging user and distribution list objects. Client applications use these entry identifiers to open and access the objects to which they are assigned.
  
The address book makes use of three other types of identifiers to represent objects:
  
- One-off entry identifiers
    
- One-off template entry identifiers
    
- Template identifiers
    
Because of the variety of entry identifiers and the similarity with which they are named, it is easy to become confused about how each type is used and created. 
  
A one-off entry identifier is an entry identifier that is used to open and access the type of recipient known as a one-off, or custom recipient. One-offs are recipients that do not belong to any of the address book providers in the profile. The entry identifiers assigned to one-offs use a format specifically reserved for one-off recipients. Because one-off entry identifiers are used to open and access objects, they are stored in the PR_ENTRYID property.
  
One-offs and one-off entry identifiers are created:
  
- When users of a client application elect to add a recipient that does not represent any entry in the address book to a message's recipient list.
    
- When users of a client application elect to add a recipient that does not represent any entry in the address book to a modifiable address book container.
    
- When a transport provider receives a message with an address that cannot be handled by its related address book provider.
    
- When a transport provider receives a message with an address that belongs to a gateway.
    
In the first two situations, the client calls **IAddrBook::CreateOneOff** to associate a one-off entry identifier with the newly created one-off recipient. In the second two situations, the transport provider calls **IMAPISupport::CreateOneOff** to associate a one-off entry identifier with the foreign address. For more information, see [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md) and [IMAPISupport::CreateOneOff](imapisupport-createoneoff.md).
  
A one-off template entry identifier is a short-term entry identifier that is used to open and access a template for creating one-offs. Both address book providers and MAPI supply templates for entering the information that is required to create a recipient of a particular type. Information about these templates, including their entry identifiers, is published in the one-off table. One-off tables are displayed when MAPI calls either the **IABLogon::GetOneOffTable** method or an address book container's **IMAPIProp::OpenProperty** method to request the **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property or when a provider calls **IMAPISupport::GetOneOffTable**. For more information, see [IABLogon::GetOneOffTable](iablogon-getoneofftable.md), [IMAPIProp::OpenProperty](imapiprop-openproperty.md), and [IMAPISupport::GetOneOffTable](imapisupport-getoneofftable.md).
  
To create a new one-off, a user selects one of the templates listed in the one-off table. The client passes the PR_ENTRYID column from the selected row, which is the one-off template entry identifier of the selected template, to **IAddrBook::NewEntry** in the  _lpEIDNewEntryTpl_ parameter. For more information, see [IAddrBook::NewEntry](iaddrbook-newentry.md). MAPI uses the one-off template entry identifier to display the template and to allow the user to enter the information needed to create the recipient. 
  
A template identifier is an entry identifier that some address book providers assign to their recipients in addition to the entry identifier that is kept in the PR_ENTRYID property. Providers set a recipient's **PR_TEMPLATEID** ([PidTagTemplateid](pidtagtemplateid-canonical-property.md)) property to store its template identifier. Some address book providers assign the same value for a recipient's template identifier and entry identifier properties.
  
Template identifiers are used only by address book providers and by MAPI to bind recipient data in one provider, referred to as the host provider, to code for the recipient in another provider, referred to as the foreign provider. The host provider supplies the storage for the recipient; the foreign provider supplies the logic. The binding process enables a host provider to update the data of a recipient that it stores using the code of a foreign provider.
  
When the host provider is ready to modify its recipient, it passes the PR_TEMPLATEID property in a call to the **IMAPISupport::OpenTemplateID** method to initiate the binding process. MAPI continues the process by transferring the template identifier to the appropriate foreign provider through a call to its **IABLogon::OpenTemplateID** method. For more information, see [IMAPISupport::OpenTemplateID](imapisupport-opentemplateid.md) and [IABLogon::OpenTemplateID](iablogon-opentemplateid.md). The foreign provider returns a pointer to its **IMAPIProp** implementation for the recipient, which the host provider can use in place of its own implementation. 
  

