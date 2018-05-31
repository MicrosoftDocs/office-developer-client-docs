---
title: "IMAPIFormInfo  IMAPIProp"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormInfo
api_type:
- COM
ms.assetid: a9fda518-11ba-42aa-85ef-dd2279e0319d
description: "Last modified: March 09, 2015"
---

# IMAPIFormInfo : IMAPIProp

  
  
**Applies to**: Outlook 
  
Gives client applications access to properties that are particular to form definition. By keeping form information in a separate object, the form library provider can describe a form to a client without activating the form.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiform.h  <br/> |
|Exposed by:  <br/> |Form information objects  <br/> |
|Implemented by:  <br/> |Form library providers  <br/> |
|Called by:  <br/> |Client applications  <br/> |
|Interface identifier:  <br/> |IID_IMAPIFormInfo  <br/> |
|Pointer type:  <br/> |LPMAPIFORMINFO  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable order

|||
|:-----|:-----|
|[CalcFormPropSet](imapiforminfo-calcformpropset.md) <br/> |Returns a pointer to the complete set of properties that a form uses.  <br/> |
|[CalcVerbSet](imapiforminfo-calcverbset.md) <br/> |Returns a pointer to the complete set of verbs that a form uses.  <br/> |
|[MakeIconFromBinary](imapiforminfo-makeiconfrombinary.md) <br/> |Builds an icon from an icon property of a form.  <br/> |
|[SaveForm](imapiforminfo-saveform.md) <br/> |Saves a description of a particular form in a configuration file.  <br/> |
|[OpenFormContainer](imapiforminfo-openformcontainer.md) <br/> |Returns a pointer to the form container in which a particular form is installed.  <br/> |
   
## Remarks

Unlike most interfaces defined in the MapiForm.h header file, **IMAPIFormInfo** inherits from the [IMAPIProp](imapipropiunknown.md) interface, because it exports most form information through calls to the [IMAPIProp::GetProps](imapiprop-getprops.md) method. 
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

