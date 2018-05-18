---
title: "MAPI String Properties"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 63d7360a-e3a3-4365-9d46-50df1c715bde
description: "Last modified: July 23, 2011"
 
 
---

# MAPI String Properties

  
  
**Applies to**: Outlook 
  
MAPI provides three different property types to describe string properties:
  
PT_TSTRING
  
PT_STRING8
  
PT_UNICODE
  
String properties are most commonly defined as PT_TSTRING. The PT_TSTRING property type conditionally compiles to one of the other string property types, depending depending on whether the UNICODE macro has been defined. PT_STRING8 describes 8-bit null-terminated character strings in the ANSI format; PT_UNICODE describes double-byte null-terminated character strings. 
  
Either a client or a service provider, or both client and provider can choose to support Unicode character strings. It is not required. A client that supports only PT_STRING8 strings can operate with a provider that supports Unicode and vice versa. To enable this interoperability, clients and service providers pass a flag, the MAPI_UNICODE flag, to indicate that Unicode is supported in methods that involve the exchange of character strings. 
  
For example, suppose a client supports Unicode and needs to retrieve the display name of a folder. All of the client's PT_TSTRING properties are compiled to type PT_UNICODE. When the client calls the folder's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve its **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) property, it passes the MAPI_UNICODE flag to request that the display name string be returned in the Unicode format. 
  
Clients and service providers need to be aware that specifying a character set in a method call is only a request. Supporting one or both character sets is up to the implementer of the object. However, service providers are encouraged to support both character sets because it allows them to achieve more widespread distribution than providers that support only one set. 
  
String properties can grow to be quite large as can binary properties — properties that use the property type PT_BINARY. To ease working with large properties, MAPI allows service providers setting these properties to enforce size limits. These limits can vary, depending on:
  
- Whether the properties are being read or written.
    
- How the service provider implements the **IMAPIProp** methods. 
    
- Runtime considerations, such as memory constraints.
    
- Character set translation issues. 
    
Size limits can also be placed on string and binary properties when they are used in the column set of a table because it is sometimes impossible to make all of a large property's value visible. Many service providers truncate large string or binary properties that are used in tables to 255 bytes. 
  
When a client calls an object's **GetProps** or **SetProps** method to work with a large string or binary property and the call fails because of the property size, the method returns the error value MAPI_E_NOT_ENOUGH_MEMORY. If it is **GetProps** that is failing for a specific property, the client can recover by calling [IMAPIProp::OpenProperty](imapiprop-openproperty.md) and requesting the **IStream** for access by specifying IID_IStream as the interface identifier. Using **OpenProperty**, the client can retrieve a large property using an interface such as **IStream** that is better suited for working with large properties. 
  
## See also



[MAPI Property Overview](mapi-property-overview.md)

