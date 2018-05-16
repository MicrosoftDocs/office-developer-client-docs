---
title: "Display Table Implementation"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: eb17675a-35e0-4545-b394-789d343510aa
description: "Last modified: July 23, 2011"
 
 
---

# Display Table Implementation

  
  
**Applies to**: Outlook 
  
A display table is used to show a property sheet, a special dialog box that is composed of one or more tabbed property pages dedicated to displaying and possibly editing one or more properties. Associated with every display table is an [IAttach : IMAPIProp](iattachimapiprop.md) interface implementation. The [IMAPIProp](imapipropiunknown.md) implementation maintains the property data that is presented in the property sheet. 
  
The rows in a display table represent the controls in the property sheet. Most controls can be associated with properties maintained with the **IMAPIProp** implementation. When a user changes the value of a modifiable control, the corresponding property is updated. 
  
The columns in a display table represent properties of the control, such as its position in the property sheet, its type, associated structure, and identifier. For a complete list of required display table columns, see [Display Tables](display-tables.md).
  
MAPI displays a property sheet to the user of a client application by reading property values from the **IMAPIProp** implementation associated with the display table or from the display table directly. As the user works with the property sheet, changing values in the controls, MAPI calls [IMAPIProp::SetProps](imapiprop-setprops.md) to save a changed control if the control's DT_SET_IMMEDIATE flag is set. For controls without the DT_SET_IMMEDIATE flag set, changes to properties are saved when the user dismisses the dialog box by clicking the **OK** or **Apply Now** button. When either of these buttons or the **Cancel** button is clicked, MAPI removes the property sheet from view. 
  
MAPI gains access to your display table either by calling the [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method in the **IMAPIProp** implementation and requesting the **PR_DETAILS_TABLE** ( [PidTagDetailsTable](pidtagdetailstable-canonical-property.md)) property or by inheriting it in a call that you have made to MAPI, such as [IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md).
  
The first access technique is used when address book providers are asked to show details about messaging users or distribution lists. The following processing occurs:
  
1. A client calls the [IAddrBook::Details](iaddrbook-details.md) method. 
    
2. MAPI calls the address book provider's [IABLogon::OpenEntry](iablogon-openentry.md) method to access the messaging user that represents the selected entry. 
    
3. MAPI calls the messaging user's [IMAPIProp::OpenProperty](imapiprop-openproperty.md) method to retrieve the **PR_DETAILS_TABLE** property, the display table for the details dialog box. 
    
4. MAPI displays the dialog box, handling the user's interaction with the information, and removes it when the user has finished. 
    
## See also

#### Concepts

[MAPI Service Providers](mapi-service-providers.md)

