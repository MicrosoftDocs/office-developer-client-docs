---
title: "Creating a Recipient"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 586c901f-d9f9-44f2-a328-051775a81265
description: "Last modified: March 09, 2015"
 
 
---

# Creating a Recipient

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Clients create recipients when they are addressing messages and when they are adding entries to modifiable address book containers. MAPI provides three methods for creating recipients:
  
- [IAddrBook::CreateOneOff](iaddrbook-createoneoff.md)
    
- [IAddrBook::NewEntry](iaddrbook-newentry.md)
    
- [IABContainer::CreateEntry](iabcontainer-createentry.md)
    
Call **IAddrBook::CreateOneOff** when you are creating recipients to be used to address messages. **CreateOneOff** creates a specially formatted one-off entry identifier to be associated with an address of a particular address type. For more information about one-offs and one-off entry identifiers, see [One-Off Addresses](one-off-addresses.md) and [One-Off Entry Identifiers](one-off-entry-identifiers.md).
  
Call **IAddrBook::NewEntry** when you are creating recipients to be used either to address messages or to add to a container. **NewEntry** has three pairs of parameters that contain entry identifiers. These parameters are described as follows: 
  
|**Parameter pair**|**Description**|
|:-----|:-----|
| _cbEidContainer_ and  _lpEidContainer_ <br/> |Entry identifier for the container into which the new entry should be placed.  <br/> |
| _cbEidNewEntryTpl_ and  _lpEidNewEntryTpl_ <br/> |Entry identifier for the template to be used to create the new entry.  <br/> |
| _lpcbEidNewEntry_ and  _lppEidNewEntry_ <br/> |Entry identifier for the new entry.  <br/> |
   
To create a recipient for an outgoing message, set  _cbEidContainer_ to zero and  _lpEidContainer_ to NULL. **NewEntry** creates a recipient with an entry identifier that conforms to the one-off format, the same type of recipient that is produced by a call to **IAddrBook::CreateOneOff**. 
  
To create a recipient to be inserted into a particular container, set  _lpEidContainer_ to the container's entry identifier and  _cbEidContainer_ to the number of bytes in the container's entry identifier. 
  
To use a template to create a recipient, set  _lpEidNewEntryTpl_ to the entry identifier of the template to be used and  _cbEidNewEntryTpl_ to the count of bytes in this entry identifier. Most modifiable address book containers support one or more templates for creating entries of a particular type. One-off templates are typically, but not always, dialog boxes. Entering information into the template produces a recipient with an address that is correctly formatted for the type. 
  
Obtain the template entry identifier from either:
  
- The **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) column in the container's one-off table, accessed by calling the container's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method and specifying **PR_CREATE_TEMPLATES** ([PidTagCreateTemplates](pidtagcreatetemplates-canonical-property.md)) as the property tag and IID_IMAPITable as the interface identifier. 
    
- An address book provider's **PR_DEF_CREATE_MAILUSER** ([PidTagDefCreateMailuser](pidtagdefcreatemailuser-canonical-property.md)) and **PR_DEF_CREATE_DL** ([PidTagDefCreateDl](pidtagdefcreatedl-canonical-property.md)) properties which hold the entry identifiers for the provider's messaging user object and distribution list templates. 
    
> [!NOTE]
> Do not confuse a new entry template's entry identifier with a different type of entry identifier called a template identifier. A template identifier is used only by providers to maintain entries copied from other providers; it is never used by clients and it is not used to create new entries. 
  
To enable the user to determine the type of entry to be created, pass zero for  _cbEidNewEntryTpl_ and NULL for  _lpEidNewEntryTpl_. When this occurs, **NewEntry** displays a common dialog box built from MAPI's one-off table — a hierarchical list of all of the templates supported by each address book provider in the profile. 
  
When an address type has been determined, either through the setting of the  _lpEidNewEntryTpl_ parameter or a selection by the user from the one-off table display, **NewEntry** displays the corresponding template using its display table. All new entry templates support the **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property. 
  
To have **NewEntry** return the entry identifier of the created entry, pass a valid address for the  _lpcbEidNewEntry_ and  _lppEidNewEntry_ parameters. MAPI places the new entry identifier at the address pointed to by  _lppEidNewEntry_ and the byte count of the new entry identifier at the address pointed to by  _lpcbEidNewEntry_.
  
Call [IABContainer::CreateEntry](iabcontainer-createentry.md) to create a recipient and save it into a particular address book container. You can use this method only with modifiable containers — containers that have the AB_MODIFIABLE flag set in their **PR_CONTAINER_FLAGS** ([PidTagContainerFlags](pidtagcontainerflags-canonical-property.md)) property. Address book providers with nonmodifiable containers do not support this method. Specify the entry identifier of the template for creating an entry of the desired type in the  _lpEntryID_ parameter. 
  
In the  _ulCreateFlags_ parameter, specify the type of duplicate entry checking required and whether or not new entries should replace existing ones. If **CreateEntry** fails to create a new object because of the duplicate entry checking imposed by the provider, do not expect to see an error or warning returned. Under these conditions, providers return a success code. 
  
If you are working directly with a container and you know exactly the types of addresses that the container can create, you can call **IABContainer::CreateEntry** and pass the entry identifier for the appropriate template. The address book provider sets some initial default properties; you can call **SetProps** to set others. The user is never involved. 
  

