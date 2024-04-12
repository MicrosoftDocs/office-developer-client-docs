---
title: "One-Off Tables"
description: "A one-off table contains information about the templates that an address book provider supports for creating new recipients."
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 0f2040b7-9b6c-4eae-aa68-29c4f7b8bd76
 
 
---

# One-Off Tables

**Applies to**: Outlook 2013 | Outlook 2016 
  
A one-off table contains information about the templates that an address book provider supports for creating new recipients. One-off tables are implemented by address book providers, individual address book containers, and by MAPI, and can be persistent or temporary. 
  
> [!NOTE]
> Do not confuse the templates in one-off tables with template identifiers; while their purposes are similar, their code constructs are nothing alike. Templates are used to create recipients of a particular type while template identifiers are used to bind the data of one recipient that belong to a host provider with code to support another recipient that belong to a foreign provider. 
  
Clients create new recipients:
  
- To add to the recipient list of an outgoing message.
    
- To add to one of the containers in the address book.
    
In both scenarios, an address book provider is asked to return a one-off table. Address book providers can implement either a single one-off table to be used in both situations or a unique one-off table for each situation. 
  
When the recipient will be included with an outgoing message, MAPI calls the address book provider's [IABLogon::GetOneOffTable](iablogon-getoneofftable.md) method to retrieve its one-off table. The one-off table includes templates which enable a user to enter information resulting in the creation of a recipient with a valid address. MAPI registers for notifications on this table, keeping it open so that changes can be reflected to the user. MAPI releases the table only when its subsystem or address book status object's [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method is called. 
  
When the recipient will be added to a container, MAPI makes a different call, invoking the container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to retrieve its **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) property. The set of templates included in this one-off table represents the types of recipients that can be added to the container. For example, mail servers often expose one container for every gateway that is installed so that each container only holds addresses specific to the corresponding gateway.
  
MAPI provides a one-off table that includes its own templates as well as templates from each of the address book providers in the session. MAPI provides a generic template that can be used to create a new recipient for any address type, assuming that the user knows its format. Address book providers use this one-off table by calling [IMAPISupport::GetOneOffTable](imapisupport-getoneofftable.md). Each of the templates included in the MAPI one-off table results in the creation of recipients with valid recipient addresses.
  
Address book providers typically supply one template for every address type they support. However, support for templates is not required. Address book providers that do not allow the creation of new addresses can return MAPI_E_NO_SUPPORT when MAPI calls to request a one-off table. Address book providers that do allow new address creation but do not supply any templates can call **IMAPISupport::GetOneOffTable** to use the templates listed in the MAPI one-off table. 
  
The following properties make up the required column set in one-off tables:
  
- **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md))
    
- **PR_DEPTH** ([PidTagDepth](pidtagdepth-canonical-property.md))
    
- **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md))
    
- **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md))
    
- **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))
    
- **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))
    
- **PR_SELECTABLE** ([PidTagSelectable](pidtagselectable-canonical-property.md))
    
 **PR_ADDRTYPE** indicates the type of address that can be associated with the new recipient created with the template. 
  
 **PR_DISPLAY_NAME** and **PR_DISPLAY_TYPE** associate data with the new recipient. **PR_DISPLAY_NAME** contains a character string that identifies the new recipient and **PR_DISPLAY_TYPE** contains a constant that identifies the type of icon to be displayed with the row. Templates for messaging users have their **PR_DISPLAY_TYPE** column set to DT_MAILUSER; templates for distribution lists have their **PR_DISPLAY_TYPE** column set to DT_DISTLIST. 
  
 **PR_ENTRYID** is the entry identifier of the template to be used to create a new recipient. This entry identifier can be passed to future [IAddrBook::NewEntry](iaddrbook-newentry.md), [IAddrBook::OpenEntry](iaddrbook-openentry.md), and [IABContainer::CreateEntry](iabcontainer-createentry.md) calls. Containers set the **PR_ENTRYID** column of their row for the default messaging user template to **PR_DEF_CREATE_MAILUSER** ([PidTagDefCreateMailuser](pidtagdefcreatemailuser-canonical-property.md)) and the **PR_ENTRYID** column of their row for the default distribution list template to **PR_DEF_CREATE_DL** ([PidTagDefCreateDl](pidtagdefcreatedl-canonical-property.md)). 
  
 **PR_DEPTH** is used to support the hierarchical display of the entries in a one-off table by indicating the level of indentation for the template. Although one-off tables can be displayed either as a flat list or a hierarchical display, the latter is preferable and address book providers should support it by setting the **PR_DEPTH** column for each row appropriately. **PR_DEPTH** is zero-based; rows with a value of 0 in their **PR_DEPTH** column are not indented. The higher the value of **PR_DEPTH**, the more the row is indented. For example, rows with **PR_DEPTH** set to 1 are indented one tab while rows with **PR_DEPTH** set to 3 are indented three tabs. 
  
 **PR_SELECTABLE** is used to indicate whether a row in the table represents a template that can be selected and used to create a new recipient. Although most rows in a one-off table do represent templates, providers can include non-template rows. For example, a provider might want to organize the one-off table by template type, including a category row that appears in the display but is not used for recipient creation. 
  
## See also



[MAPI Tables](mapi-tables.md)

