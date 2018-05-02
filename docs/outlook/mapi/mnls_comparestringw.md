---
title: "MNLS_CompareStringW"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f8d0b7b9-2798-4d29-99e4-17da99039361
description: "Last modified: February 20, 2012"
---

# MNLS_CompareStringW

 **Last modified:** February 20, 2012 
  
 * **Applies to:** Outlook * 
  
Compares two Unicode strings.
  
```
int MNLS_CompareStringW (
  LCID lcid,
  DWORD dwFlags,
  LPCWSTR pstr1,
  int cch1,
  LPCWSTR pstr2,
  int cch2);
```

## Parameters

 _lcid_
  
> [in] Locale identifier. For detailed definitions, see the  _Locale_ parameter of [CompareString](http://msdn.microsoft.com/en-us/library/dd317759%28VS.85%29.aspx).
    
 _dwFlags_
  
> [in] Flags to ignore case and diacritics. For detailed definitions, see the  _dwCmpFlags_ parameter of [CompareStringEx](http://msdn.microsoft.com/en-us/library/dd317761%28VS.85%29.aspx).
    
 _pstr1_
  
> [in] Pointer to the first Unicode string to compare.
    
 _cch1_
  
> [in] Length in characters of the first Unicode string, excluding the terminating null character. The application can supply a negative value if the string is null-terminated. In this case, the **MNLS_CompareStringW** function determines the length automatically. 
    
 _pstr2_
  
> [in] Pointer to the second Unicode string to compare.
    
 _cch2_
  
> [in] Length in characters of the second Unicode string, excluding the terminating null character. The application can supply a negative value if the string is null-terminated. In this case, the function determines the length automatically.
    
## Return value

Returns the values described for [CompareStringEx](http://msdn.microsoft.com/en-us/library/dd317761%28VS.85%29.aspx).
  
## Remarks

This function wraps [CompareStringW](http://msdn.microsoft.com/en-us/library/dd317759%28VS.85%29.aspx). **MNLS_CompareStringW** takes the same parameters and has the same behavior as [CompareStringW](http://msdn.microsoft.com/en-us/library/dd317759%28VS.85%29.aspx).
  
## See also

#### Other resources

[CompareStringW](http://msdn.microsoft.com/en-us/library/dd317759%28VS.85%29.aspx)
  
[CompareStringEx](http://msdn.microsoft.com/en-us/library/dd317761%28VS.85%29.aspx)

