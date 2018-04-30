---
title: "Displaying Configuration Property Sheets"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: c9386b98-615f-488c-8212-11d9abebbdcf
description: "Last modified: July 23, 2011"
---

# Displaying Configuration Property Sheets

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Transport providers use the [IMAPISupport::DoConfigPropsheet](imapisupport-doconfigpropsheet.md) method to implement configuration property sheets. When calling **DoConfigPropSheet**, the transport provider passes in a pointer to an array of properties along with information about how to display them. MAPI then presents the properties to the user by means of a standard dialog box. You are strongly encouraged to use this property sheet mechanism when implementing your transport provider due to the benefit to the user of a consistent interface.
  
## Transport Providers

Transport providers can use the [BuildDisplayTable](builddisplaytable.md) function to simplify construction of a display table for use with **DoConfigPropSheet**. Transport providers can also use the property sheet API directly. To buffer changes to the properties, transport providers can use the [CreateIProp](createiprop.md) function. This simplifies the handling of cancellations by the user while the user modifies the values stored in the properties. If necessary, a transport provider can also provide a wizard dialog box to simplify configuration tasks for the user. 
  

