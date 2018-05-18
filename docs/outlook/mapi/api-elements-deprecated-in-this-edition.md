---
title: "API Elements Deprecated in This Edition"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: d0a6d182-961c-4496-a3bd-f643612527a5
description: "Last modified: June 25, 2012"
 
 
---

# API Elements Deprecated in This Edition

  
  
**Applies to**: Outlook 
  
The following API elements are deprecated in Microsoft Outlook 2013. They are no longer supported and you should not use them in new projects.
  
## Deprecation of Message and Recipient Options

The following API elements are deprecated in this release because of obsolete message and recipient options:
  
- **IXPLogon::RegisterOptions**—The MAPI subsystem no longer calls this method to establish any default values for message and recipient options for a transport provider.
    
- **OPTIONDATA**—This data structure that supported properties for message and recipient options is obsolete. The MAPI subsystem no longer calls **IXPLogon::RegisterOptions** to obtain any message or recipient options that a transport provider supports for a particular address type. 
    
- **OPTIONCALLBACK**—This function prototype, which a transport provider used to declare a callback function and which, in turn, the MAPI subsystem used to resolve the provider's properties, is obsolete. The MAPI subsystem no longer calls **IXPLogon::RegisterOptions** or uses any callback function returned by the transport provider. 
    
- **IMAPISession::MessageOptions**—MAPI client and service providers should no longer call this method to display properties or let users set properties that control a particular message and address type. The method always returns MAPI_E_NOT_FOUND, which indicates that there are no message options for the particular message.
    
- **IMAPISession::QueryDefaultMessageOpt**—MAPI client and service providers should no longer call this method to retrieve properties that control message options for a particular address type. The method no longer returns a pointer to any array of property values.
    
- **IAddrBook::RecipOptions**—MAPI client and service providers should no longer call this method to display properties or let users set properties that control processing for a recipient of a particular address type. The method always returns MAPI_W_ERRORS_RETURNED, which indicates that there are no recipient options for the particular recipient.
    
- **IAddrBook::QueryDefaultRecipOpt**—MAPI client and service providers should no longer call this method to retrieve properties that control recipient options for a particular address type. The method no longer returns a pointer to any array of property values.
    
## See also



[Getting Started with the Outlook MAPI Reference](getting-started-with-the-outlook-mapi-reference.md)

