---
title: "Implementing One-Off Tables"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 57933d44-d47a-4e7f-ba95-b49b4934d0a5
description: "Last modified: July 23, 2011"
 
 
---

# Implementing One-Off Tables

  
  
**Applies to**: Outlook 
  
Your provider might implement one or more one-off tables. A one-off table is a summary list of one-off templates used to create recipients, either directly into a container or into the recipient list of an outgoing message. A one-off template is a form users employ for entering data relevant to a particular type of address. When the user is finished working with the template, your provider creates the new recipient and adds it to the message. Typically each template handles a single address type. However, it is possible for a template to handle multiple types or for multiple templates to handle the same type. 
  
Your provider must support the **OpenEntry** method for each template that it includes in the one-off table. The implementation of **OpenEntry** should retrieve a display table for the template. MAPI uses the display table to make the template visible to the user. 
  
Although most of the rows in one-off tables represent templates, some of the rows can be used to categorize, or group, templates. Whether or not a row in a one-off table represents a template is indicated by the value of its **PR_SELECTABLE** ([PidTagSelectable](pidtagselectable-canonical-property.md)) column. Rows that represent templates have the PR_SELECTABLE column set to TRUE; rows that do not represent templates have it set to FALSE.
  
MAPI defines three types of one-off tables:
  
- A one-off table that reflects the templates that an individual container supports
    
- A one-off table that reflects all of the templates that your provider supports 
    
- A one-off table that reflects all of the templates that all of the providers in the profile support plus some that MAPI supports
    
The first two types are implemented by providers that support the creation recipients, either onto a message or into a container. Your provider can include the same set or a different set of templates in its one-off tables. The main difference between the two types is that your provider table should include templates for creating recipients that can be used on outgoing messages and your container table should include templates for creating recipients to be added to your container. A container may only support a restricted set of templates, but the provider one-off table should include every template the provider supports.
  
The third type of one-off table is implemented by MAPI; providers gain access to it by calling [IMAPISupport::GetOneOffTable](imapisupport-getoneofftable.md). The MAPI one-off table is the union of all of the provider tables; it includes every template supported by every provider in the profile. It also includes templates supported by MAPI. Your provider can use this table in place of the table requested for a container. However, the templates in this table can also be used for creating recipients for outgoing messages.
  

