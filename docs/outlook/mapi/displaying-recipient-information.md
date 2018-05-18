---
title: "Displaying Recipient Information"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 7ffec274-ee90-44c7-ab2e-7dfb502517a6
description: "Last modified: July 23, 2011"
 
 
---

# Displaying Recipient Information

  
  
**Applies to**: Outlook 
  
MAPI provides a common dialog box for showing recipient details. The details dialog box is created from a display table and an **IMAPIProp** implementation. The display table describes the appearance of the details display and the **IMAPIProp** implementation controls the data for the recipient. Your provider is responsible for supplying the display table and the **IMAPIProp** implementation for each recipient. 
  
The easiest way to create the display table is to define a [DTPAGE](dtpage.md) structure and call [BuildDisplayTable](builddisplaytable.md). However, some providers, specifically read-only providers that allow the creation of one-off recipients, use **IPropData**. The **IMAPIProp** implementation can be any type of property object. 
  
There are two methods for invoking this dialog box: [IAddrBook::Details](iaddrbook-details.md) and [IMAPISupport::Details](imapisupport-details.md). When your provider calls one of these methods to request details for a recipient, MAPI first opens the recipient by calling its container's [IMAPIContainer::OpenEntry](imapicontainer-openentry.md) method. Next it calls the recipient's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to request the **PR_DETAILS_TABLE** ([PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property. **PR_DETAILS_TABLE** is the property that represents a recipient's details display table. 
  
The [IPropData : IMAPIProp](ipropdataimapiprop.md) interface can be used to monitor changes on display table controls as described in the following procedure. 
  
 **To monitor changes to a control**
  
1. Before the user gains access to the control, call [IPropData::HrSetObjAccess](ipropdata-hrsetobjaccess.md) to set the control's access to IPROP_CLEAN. 
    
2. Allow the user to work with the dialog box. 
    
3. When the user has finished, call [IPropData::HrGetPropAccess](ipropdata-hrgetpropaccess.md) to retrieve the current access level of the control. 
    
4. If the access level is IPROP_DIRTY, the user has modified the control. Your provider should:
    
  - Call [IPropData::HrSetPropAccess](ipropdata-hrsetpropaccess.md) to set the access level back to IPROP_CLEAN. 
    
  - Call the property data object's [IMAPIProp::GetProps](imapiprop-getprops.md) method to retrieve the changed property and update it by calling [IMAPIProp::SetProps](imapiprop-setprops.md).
    
5. If the access level is still IPROP_CLEAN, the control has not been modified. 
    
For more information about creating display tables, see [Display Tables](display-tables.md).
  

