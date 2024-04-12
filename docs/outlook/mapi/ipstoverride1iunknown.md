---
title: "IPSTOVERRIDE1  IUnknown"
description: "IPSTOVERRIDE1 IUnknown allows a Personal Folders file (PST) store provider to override the PSTDisableGrow policy."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IPSTOVERRIDE1
api_type:
- COM
ms.assetid: d26cee81-45ea-4fd3-8a54-5f35264b5d6a
---

# IPSTOVERRIDE1 : IUnknown

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Allows a Personal Folders file (PST) store provider to override the PSTDisableGrow policy.
  
|Property |Value |
|:-----|:-----|
|Inherits from:  <br/> |IUnknown  <br/> |
|Implemented by:  <br/> |PST store provider  <br/> |
|Called by:  <br/> |Client  <br/> |
|Interface identifier:  <br/> |IID_IPSTOVERRIDE1  <br/> |
   
## Vtable order

|Member |Description |
|:-----|:-----|
|[IPSTOVERRIDE1::GetPersistedRegistrations](ipstoverride1-getpersistedregistrations.md) <br/> |Retrieves the list of registrations for the Personal Folders (.pst) file. |
|[IPSTOVERRIDE1::SetPersistedRegistrations](ipstoverride1-setpersistedregistrations.md) <br/> |Registers Personal Folders files for automatic unlocking, avoiding further calls to HrTrustedPSTOverrideHandlerCallback. |
|[IPSTOVERRIDE1::OverridePSTDisableGrow](ipstoverride1-overridepstdisablegrow.md) <br/> |Unlocks a Personal Folders file for growth. |
   
## Remarks

The PST Override Handler Interface Identifiers might not be defined in the downloadable header file you currently have, in which case you will find them in the [MAPI Constants](mapi-constants.md) topic, and can copy and add them to your code. Use the DEFINE_GUID macro defined in the Microsoft Windows Software Development Kit (SDK) header file guiddef.h to associate globally unique identifier (GUID) symbolic names with their values. 
  
<!-- For more information see [How to implement a PST override handler to bypass the PSTDisableGrow policy in Outlook 2007](https://support.microsoft.com/kb/956070). -->
  
## See also



[IPSTOVERRIDEREQ : IUnknown](ipstoverridereqiunknown.md)

