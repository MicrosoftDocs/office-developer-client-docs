---
title: "Strategies for Error Handling"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: be941efd-04b3-48d0-9b9c-8195ad2bb58d
description: "Last modified: July 23, 2011"
---

# Strategies for Error Handling

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Because interface methods are virtual, it is not possible to know, as a caller, the full set of values that can be returned from any one call. One implementation of a method might return five values; another might return eight. The reference entries in the MAPI documentation list a few values that can be returned for each method; these are the values that your client or service provider can check for and handle because they have special meanings. Other values can be returned, but because they are not meaningful, special code to handle those is not necessary. A simple check for success or failure is adequate.
  
A few of the interface methods return warnings. If a method that your client or service provider calls can return a warning, use the **HR_FAILED** macro to test the return value rather than a check for zero or nonzero. Warnings, although nonzero, differ from error codes in that they do not have the high bit set. If your client or service provider does not use the macro, it is likely that a warning might be mistaken for a failure. 
  
Although most interface methods and functions return HRESULT values, some functions return unsigned long values. Also, some methods used in the MAPI environment come from COM and return COM error values rather than MAPI error values. Keep in mind the following guidelines when making calls:
  
- Never rely on or use the return values from **IUnknown::AddRef** or **IUnknown::Release**. These return values are for diagnostic purposes only. 
    
- **IUnknown::QueryInterface** always returns generic COM errors where the facility is FACILITY_NULL or FACILITY_RPC, rather than MAPI errors. 
    
- All other interface methods return MAPI interface errors with a facility of FACILITY_ITF, or FACILITY_RPC or FACILITY_NULL errors.
    
When a call is made to an unsupported MAPI method, one of four possible errors can be returned: 
  
MAPI_E_NO_SUPPORT
  
MAPI_E_INTERFACE_NOT_SUPPORTED
  
MAPI_E_INVALID_PARAMETER
  
MAPI_E_VERSION. 
  

