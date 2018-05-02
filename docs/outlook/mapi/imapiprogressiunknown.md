---
title: "IMAPIProgress  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProgress
api_type:
- COM
ms.assetid: 7a872296-0378-456f-b4d6-cb4d96b09d6e
description: "Last modified: March 09, 2015"
---

# IMAPIProgress : IUnknown

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Implements a progress object that provides client applications with a progress indicator. A progress indicator is a user-interface display that shows the percentage of completion of an operation, such as copying folders between message stores. MAPI and client applications implement progress objects and service providers use them. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Progress objects  <br/> |
|Implemented by:  <br/> |MAPI and client applications  <br/> |
|Called by:  <br/> |Service providers  <br/> |
|Interface identifier:  <br/> |IID_IMAPIProgress  <br/> |
|Pointer type:  <br/> |LPMAPIPROGRESS  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[Progress](imapiprogress-progress.md) <br/> |Updates the progress indicator with a display of the progress as it is made toward completion of the operation.  <br/> |
|[GetFlags](imapiprogress-getflags.md) <br/> |Returns flag settings from the progress object for the level of operation on which progress information is calculated.  <br/> |
|[GetMax](imapiprogress-getmax.md) <br/> |Returns the maximum number of items in the operation for which progress information is displayed.  <br/> |
|[GetMin](imapiprogress-getmin.md) <br/> |Returns the minimum value in the [SetLimits](imapiprogress-setlimits.md) method for which progress information is displayed.  <br/> |
|[SetLimits](imapiprogress-setlimits.md) <br/> |Sets the lower and upper limits for the number of items in the operation, and the flags that control how progress information is calculated for the operation.  <br/> |
   
## Remarks

MAPI includes an  _lpProgress_ parameter in many of the methods that perform potentially lengthy operations.  _lpProgress_ points to a client implementation of a progress object. Clients that implement the **IMAPIProgress** interface set this parameter to point to their implementation; clients that do not implement **IMAPIProgress** set the parameter to NULL. To display a progress indicator during processing of the operation, service providers use the progress object supplied by the client, if available, or a MAPI implementation (indicated when  _lpProgress_ is set to NULL). 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**Files**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MapiProgress.h and MapiProgress.cpp  <br/> |Not applicable  <br/> |If the IMAPIProgress setting is enabled, MFCMAPI will pass an **IMAPIProgress** implementation to all functions that MFCMAPI invokes that accept an implementation.  <br/> |
   
## See also

#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)
  
[MAPI Interfaces](mapi-interfaces.md)

