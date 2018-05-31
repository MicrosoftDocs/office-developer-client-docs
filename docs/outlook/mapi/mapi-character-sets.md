---
title: "MAPI Character Sets"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: fbe63916-b3eb-4ea7-bc42-80a8b0281b03
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Character Sets

  
  
**Applies to**: Outlook 
  
MAPI-compliant client applications and service providers can use ANSI characters (single byte) or Unicode characters (double byte). OEM character sets are not supported. An OEM string passed to a MAPI method or function will cause that method or function to fail. Client applications that work with filenames in the OEM character set must be careful to convert them to ANSI before passing them to a MAPI method or function.
  
Supporting the Unicode character set is optional, both for clients and service providers. All service providers should write their code so that they can compile regardless of whether or not they support Unicode. Clients compile conditionally, depending on their level of support, but service providers do not. They should not have to be recompiled when the character set changes. Nothing in service provider code should be conditional. 
  
When clients or service providers that support Unicode make a method call that includes character strings as input or output parameters, they set the MAPI_UNICODE flag. Setting this flag indicates to the implementation that all incoming strings are Unicode strings. On output, setting this flag requests that all strings passed back from the implementation should be Unicode strings if possible. Method implementers that support Unicode will comply with the request; method implementers that do not provide Unicode support will not comply. String properties that are not in Unicode format are of type PT_STRING8.
  
MAPI defines the **fMapiUnicode** constant in the header file MAPIDEFS.H to represent the default character set. If a client or service provider supports Unicode, **fMapiUnicode** is set to MAPI_UNICODE. Clients and service providers that do not support Unicode set **fMapiUnicode** to zero. 
  
Service providers that do not support Unicode should:
  
- Refuse to perform conversions between character sets.
    
- Never pass the MAPI_UNICODE flag in method calls.
    
- Return MAPI_E_BAD_CHARWIDTH when the MAPI_UNICODE flag is passed in.
    
- Declare ANSI string properties explicitly. 
    
Service providers can also return MAPI_E_BAD_CHARWIDTH when they only support Unicode and clients do not pass the MAPI_UNICODE flag. 
  
 The current version of MAPI supports Unicode in the following methods: 
  
[IAddrBook::Address](iaddrbook-address.md)
  
[IAddrBook::CreateOneOff](iaddrbook-createoneoff.md)
  
[IAddrBook::Details](iaddrbook-details.md)
  
[IAddrBook::ResolveName](iaddrbook-resolvename.md)
  
[IMAPIProp::GetLastError](imapiprop-getlasterror.md) (**IAddrBook** implementation only) 
  
For these methods, callers can expect any returned strings to be Unicode strings. Character strings returned from MAPI implementations of any other method will be ANSI character strings.
  

