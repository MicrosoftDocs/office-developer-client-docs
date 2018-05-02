---
title: "IPSTOVERRIDE1  IUnknown"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IPSTOVERRIDE1
api_type:
- COM
ms.assetid: d26cee81-45ea-4fd3-8a54-5f35264b5d6a
description: "Last modified: March 09, 2015"
---

# IPSTOVERRIDE1 : IUnknown

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Allows a Personal Folders file (PST) store provider to override the PSTDisableGrow policy.
  
|||
|:-----|:-----|
|Inherits from:  <br/> |IUnknown  <br/> |
|Implemented by:  <br/> |PST store provider  <br/> |
|Called by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IPSTOVERRIDE1  <br/> |
   
## Vtable Order

|||
|:-----|:-----|
|[IPSTOVERRIDE1::GetPersistedRegistrations](ipstoverride1-getpersistedregistrations.md) <br/> |Retrieves the list of registrations for the Personal Folders (.pst) file.  <br/> |
|[IPSTOVERRIDE1::SetPersistedRegistrations](ipstoverride1-setpersistedregistrations.md) <br/> |Registers Personal Folders files for automatic unlocking, avoiding further calls to HrTrustedPSTOverrideHandlerCallback.  <br/> |
|[IPSTOVERRIDE1::OverridePSTDisableGrow](ipstoverride1-overridepstdisablegrow.md) <br/> |Unlocks a Personal Folders file for growth.  <br/> |
   
## Remarks

The PST Override Handler Interface Identifiers might not be defined in the downloadable header file you currently have, in which case you will find them in the [MAPI Constants](mapi-constants.md) topic, and can copy and add them to your code. Use the DEFINE_GUID macro defined in the Microsoft Windows Software Development Kit (SDK) header file guiddef.h to associate globally unique identifier (GUID) symbolic names with their values. 
  
For more information see [How to implement a PST override handler to bypass the PSTDisableGrow policy in Outlook 2007](http://support.microsoft.com/kb/956070).
  
## See also

#### Reference

[IPSTOVERRIDEREQ : IUnknown](ipstoverridereqiunknown.md)

