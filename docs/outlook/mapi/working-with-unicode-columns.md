---
title: "Working with Unicode Columns"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 2cd55464-263f-4f83-b874-524271773934
description: "Last modified: July 23, 2011"
 
 
---

# Working with Unicode Columns

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Character strings in tables can be represented using standard 8-bit characters, which are property type PT_STRING8, or 16-bit Unicode characters, which are property type PT_UNICODE. Table implementers are free to choose whether or not their tables support Unicode strings. Because Unicode adds value for both clients and service providers by extending the feature set, supporting Unicode wherever possible is recommended. 
  
Many table methods accept a flag that dictates whether or not string property values are expected to be Unicode. On input, specifying the MAPI_UNICODE flag indicates to the table implementer that all string property values passed in with the call are Unicode strings and have property types of PT_UNICODE. On output, this flag indicates that all returned string property values should be Unicode strings, if possible. Whether the flag has a meaning for input or output depends on the method. Table implementers that do not support Unicode and are passed the MAPI_UNICODE flag return the MAPI_E_BAD_CHAR_WIDTH value.
  
## See also



[MAPI Tables](mapi-tables.md)

