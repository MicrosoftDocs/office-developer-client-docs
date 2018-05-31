---
title: "Displaying Table Rows and Columns"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 49567a8d-b58d-4636-bead-a1f84b4f111d
description: "Last modified: March 09, 2015"
 
 
---

# Displaying Table Rows and Columns

  
  
**Applies to**: Outlook 
  
 A property page can be used by an address book provider to enable users to define new email recipients. 
  
The corresponding display table contains four rows, one for each control. The values for the columns that indicate position are as follows.
  
|**Control**|**XPOS**|**YPOS**|**DELTAX**|**DELTAY**|
|:-----|:-----|:-----|:-----|:-----|
|Display name label  <br/> |14  <br/> |18  <br/> |49  <br/> |8  <br/> |
|Display name edit box  <br/> |76  <br/> |16  <br/> |89  <br/> |12  <br/> |
|Email address label  <br/> |14  <br/> |42  <br/> |50  <br/> |8  <br/> |
|Email address edit box  <br/> |76  <br/> |40  <br/> |89  <br/> |12  <br/> |
|Check box  <br/> |14  <br/> |64  <br/> |90  <br/> |12  <br/> |
   
This next table suggests appropriate values for the control's type, its **PR_CONTROL_TYPE** ([PidTagControlType](pidtagcontroltype-canonical-property.md)) property, and bitmask of flags, its **PR_CONTROL_FLAGS** ([PidTagControlFlags](pidtagcontrolflags-canonical-property.md)) property.
  
|**Control**|**Type**|**Flags**|
|:-----|:-----|:-----|
|Display name label  <br/> |DTCT_LABEL  <br/> |0  <br/> |
|Display name edit box  <br/> |DTCT_EDIT  <br/> |DT_EDITABLE | DT_REQUIRED  <br/> |
|Email address label  <br/> |DTCT_LABEL  <br/> |0  <br/> |
|Email address edit box  <br/> |DTCT_EDIT  <br/> |DT_EDITABLE | DT_REQUIRED  <br/> |
|Check box  <br/> |DTCT_CHECKBOX  <br/> |DT_EDITABLE  <br/> |
   
The final table lists each control with the contents of its associated control structure. Notice that the value for each of the label controls appears in memory directly following the structure.
  
|**Control**|**Structure**|
|:-----|:-----|
|Display name label  <br/> |{sizeof(DTBLLABEL), 0} "Display name:"  <br/> |
|Display name edit box  <br/> |{sizeof(DTBLEDIT), 0, 80, PR_DISPLAY_NAME}  <br/> |
|Email address label  <br/> |{sizeof(DTBLLABEL), 0} "Email address:"  <br/> |
|Email address edit box  <br/> |{sizeof(DTBLEDIT), 0, 80, PR_EMAIL_ADDRESS}  <br/> |
|Check box  <br/> |PR_SEND_RICH_INFO  <br/> |
   
> [!NOTE]
> The **OK**, **Cancel**, and **Help** buttons are not included in the display table. The user interface can add context to a dialog box by adding controls not in the display table. 
  
## See also



[Display Table Implementation](display-table-implementation.md)

