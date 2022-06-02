---
title: "Using Macros for Error Handling"
description: Outlines several macros for making it easier to work with HRESULT values in Outlook 2013 and Outlook 2016.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 351405ca-b72b-4e9e-bc8e-947344588970
 
 
---

# Using Macros for Error Handling

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
There are several macros for making it easier to work with HRESULT values.
  
There are two sets of macros that test for failure or success: HR_SUCCEEDED and HR_FAILED and SUCCEEDED and FAILED. SUCCEEDED is the same as HR_SUCCEEDED and FAILED is the same as HR_FAILED.
  
In this case, use the **ResultFromScode** macro to set the HRESULT variable to the corresponding HRESULT value for S_OK. 
  
Commonly used macros are briefly described in the following table.
  
|**Macro**|**Description**|
|:-----|:-----|
|**MAKE_HRESULT** <br/> |Constructs an HRESULT from its components. |
|**HR_SUCCEEDED** <br/> |Tests an HRESULT for a success or warning condition. |
|**HR_FAILED** <br/> |Tests an HRESULT for an error condition. |
|**HRESULT_CODE** <br/> |Extracts the error code part of the HRESULT. |
|**HRESULT_FACILITY** <br/> |Extracts the facility from the HRESULT. |
|**HRESULT_SEVERITY** <br/> |Extracts the severity bit from the SEVERITY. |
|**SUCCEEDED** <br/> |Tests an HRESULT for a success or warning condition. |
|**FAILED** <br/> |Tests an HRESULT for an error condition. |
   

