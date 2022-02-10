---
title: "IMAPIControl  IUnknown"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIControl
api_type:
- COM
ms.assetid: 5a647e15-ba22-4a7c-b235-75cd76b77c1a
description: "Last modified: March 09, 2015"
---

# IMAPIControl : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Enables and disables a button control, and performs tasks when a user of a client application clicks the enabled control. Service providers implement control objects to create custom buttons on dialog boxes, such as configuration property sheets, that are defined by using display tables. 
  
For more information about how to work with display tables and control objects, see [Display Tables](display-tables.md).
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Exposed by:  <br/> |Control objects  <br/> |
|Implemented by:  <br/> |Service providers  <br/> |
|Called by:  <br/> |MAPI  <br/> |
|Interface identifier:  <br/> |IID_IMAPIControl  <br/> |
|Pointer type:  <br/> |LPMAPICONTROL  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[GetLastError](imapicontrol-getlasterror.md) <br/> |Returns a [MAPIERROR](mapierror.md) structure that contains information about the previous button control error. |
|[Activate](imapicontrol-activate.md) <br/> |Performs a task such as displaying a dialog box or starting a programmatic operation when a client application user clicks the button control. |
|[GetState](imapicontrol-getstate.md) <br/> |Retrieves a value that indicates whether the button control is enabled or disabled. |
   
## See also



[MAPI Interfaces](mapi-interfaces.md)

