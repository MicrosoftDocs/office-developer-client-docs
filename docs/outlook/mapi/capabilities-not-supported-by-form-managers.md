---
title: "Capabilities Not Supported by Form Managers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: b51e9e03-a333-4fdc-b6fe-87bd4e947b9f
description: "Last modified: July 23, 2011"
 
 
---

# Capabilities Not Supported by Form Managers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The following features are not supported by the default form manager for performance reasons but can be supported by custom form managers.
  
- A hierarchy that enables forms to be grouped or categorized throughout a form library. A form library is a flat-file database of forms.
    
- Access control for categories of forms, corresponding to message classes or superclasses.
    
- Support for multiple language versions of the same form in a single form library.
    
These are implementation issues. There is nothing to prevent a custom form manager from implementing these features.
  
The MAPI form architecture does not support multiple form managers running concurrently. Although MAPI supports multiple concurrent message store providers, transport providers, and address book providers, only a single form manager is supported.
  
Because only one form manager may be running at once, if you implement a custom form manager you will have to re-implement any functionality from the default form manager that you need. Because your custom form manager will entirely replace the default form manager, capabilities of the default form manager will be unavailable unless they are duplicated in your custom form manager.
  
## See also



[MAPI Forms](mapi-forms.md)

