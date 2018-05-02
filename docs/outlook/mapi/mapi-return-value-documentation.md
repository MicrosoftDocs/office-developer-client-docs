---
title: "MAPI Return Value Documentation"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: c32ee53c-b063-4a00-a6bf-75ce5e07f56a
description: "Last modified: March 09, 2015"
 
 
---

# MAPI Return Value Documentation

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
The reference entries in this Reference document only those return values that require some handling by client applications. Return values that indicate common error conditions and can be deduced by checking for failure are not included in the documentation. For example, many interface methods can return MAPI_E_INVALID_PARAMETER if a caller specifies the wrong value for an input parameter. This value is typically not listed in the set of expected return values because there is no need to look specifically for MAPI_E_INVALID_PARAMETER and no need to process it differently from any other error. On the other hand, some service providers do not support event notification and will return MAPI_E_NO_SUPPORT to the **Advise** method made by clients through **IMAPISession**. Because clients need to explicitly check for this value and provide code for handling the condition that it represents should it occur, MAPI_E_NO_SUPPORT is included in the list of return values for [IMAPISession::Advise](imapisession-advise.md).
  
The following table describes error values that are commonly returned from methods and functions and require explicit handling on the part of a client or service provider. These values fall into four categories: values that indicate invalid input data, values that indicate resource problems, values that indicate character set incompatibility, and values that indicate failure of an unknown origin.
  
|**Return value**|**Description**|
|:-----|:-----|
|MAPI_E_INVALID_PARAMETER  <br/> |One or more of the parameters passed into the method or functions were not valid.  <br/> |
|MAPI_E_UNKNOWN_FLAGS  <br/> |One or more values for a flags parameter were not valid.  <br/> |
|MAPI_E_DISK_ERROR  <br/> |There was a problem writing to or reading from disk.  <br/> |
|MAPI_E_NOT_ENOUGH_DISK  <br/> |Not enough disk space was available to complete the operation.  <br/> |
|MAPI_E_NOT_ENOUGH_MEMORY  <br/> |Not enough memory was available to complete the operation.  <br/> |
|MAPI_E_NOT_ENOUGH_RESOURCES  <br/> |Not enough system resources were available to complete the operation.  <br/> |
|MAPI_E_BAD_CHARWIDTH  <br/> |An incompatibility exists in the character sets supported by the caller and the implementation.  <br/> |
|MAPI_E_CALL_FAILED  <br/> |An error of unexpected or unknown origin occurred.  <br/> |
   
The constants that represent MAPI return values are listed in the MAPICODE.H header file. Some of the constants map to Win32 errors; the mapping of these constants to numeric values can be found in the Win32 header file, WINERROR.H.
  
Errors regarding invalid data passed in by a caller can be determined through either the parameter validation API functions provided by MAPI or a set of macros. 
  
Character set incompatibility arises when either of the following situations occurs:
  
- A client or service provider sets the MAPI_UNICODE flag on a method or function call and the implementation does not support Unicode. Setting MAPI_UNICODE indicates that character strings passed in as input are Unicode strings and that character strings passed back as output are expected to be Unicode strings.
    
- A client or service provider does not set the MAPI_UNICODE flag on a method or function call and the implementation only supports Unicode.
    

