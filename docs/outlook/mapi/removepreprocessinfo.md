---
title: "RemovePreprocessInfo"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.RemovePreprocessInfo
api_type:
- COM
ms.assetid: 25f46937-abac-4a0b-83db-eeac9451c112
description: "Last modified: March 09, 2015"
---

# RemovePreprocessInfo

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Removes preprocessed information written by a [PreprocessMessage](preprocessmessage.md) based function from a message. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapispi.h  <br/> |
|Defined function implemented by:  <br/> |Transport providers  <br/> |
|Defined function called by:  <br/> |MAPI spooler  <br/> |
   
```
HRESULT RemovePreprocessInfo(
  LPMESSAGE lpMessage
);
```

## Parameters

 _lpMessage_
  
> [in] Pointer to the preprocessed message from which information is to be removed.
    
## Return value

S_OK
  
> Preprocessed information was removed successfully.
    
## Remarks

The MAPI spooler calls a function based on **RemovePreprocessInfo**. A transport provider registers the **RemovePreprocessInfo** based function at the same time it registers the parallel **PreprocessMessage** based function in a call to the [IMAPISupport::RegisterPreprocessor](imapisupport-registerpreprocessor.md) method. 
  
An image rendering suitable for fax transmission is an example of preprocessed information written by a function defined by the [PreprocessMessage](preprocessmessage.md)function prototype. The MAPI spooler usually calls a **RemovePreprocessInfo** function after sending a message that contains preprocessed information. 
  

