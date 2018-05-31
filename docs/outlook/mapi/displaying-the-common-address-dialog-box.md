---
title: "Displaying the Common Address Dialog Box"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 276f9fa8-c333-4381-b20f-22fe9d2f27cd
description: "Last modified: July 23, 2011"
 
 
---

# Displaying the Common Address Dialog Box

  
  
**Applies to**: Outlook 
  
The MAPI common address dialog box can be used for a variety of addressing tasks such as constructing a recipient list. To display this dialog box, call **IAddrBook::Address**. Depending on which of the many parameters you set and how you set them, you can limit your display to entries of a particular type from a particular container.
  
 **To limit the address dialog box to displaying personal address book (PAB) entries only**
  
1. Call [IAddrBook::GetPAB](iaddrbook-getpab.md) to retrieve the entry identifier of the PAB. 
    
2. Create a property restriction that uses RELOP_EQ for the **relop** member of the [SPropertyRestriction](spropertyrestriction.md) structure and either **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) or **PR_AB_PROVIDER_ID** ([PidTagAbProviderId](pidtagabproviderid-canonical-property.md)) as the **ulPropTag** member. If you use **PR_ENTRYID**, pass the entry identifier retrieved from **GetPAB**. If you use **PR_AB_PROVIDER_ID**, pass the value included in the MSPAB.H header file. **PR_AB_PROVIDER_ID** is the unique identifier for the PAB designed by MAPI. 
    
3. Call [IAddrBook::Address](iaddrbook-address.md) with the  _lpHierRestriction_ parameter pointing to the property restriction. 
    

