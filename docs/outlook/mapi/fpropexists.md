---
title: "FPropExists"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FPropExists
api_type:
- COM
ms.assetid: 33c00752-cdc1-4cbe-8fca-6b06c78bd362
description: "Last modified: March 09, 2015"
---

# FPropExists

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Searches for a given property tag in an [IMAPIProp](imapipropiunknown.md) interface or an interface derived from **IMAPIProp**, such as [IMessage](imessageimapiprop.md) or [IMAPIFolder](imapifolderimapicontainer.md). 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
BOOL FPropExists(
  LPMAPIPROP pobj,
  ULONG ulPropTag
);
```

## Parameters

 _pobj_
  
> [in] Pointer to the **IMAPIProp** interface or interface derived from **IMAPIProp** within which to search for the property tag. 
    
 _ulPropTag_
  
> [in] Property tag for which to search.
    
## Return value

TRUE 
  
> A match for the given property tag was found. 
    
FALSE 
  
> A match for the given property tag was not found.
    
## Remarks

If the property tag in the  _ulPropTag_ parameter has type PT_UNSPECIFIED, the **FPropExists** function looks for a match based only on the property identifier. Otherwise, the match is for the entire property tag, including the type. 
  

