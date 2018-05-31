---
title: "SERVICEWIZARDDLGPROC"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SERVICEWIZARDDLGPROC
api_type:
- COM
ms.assetid: 3e2d5190-e67a-470d-8177-0f0ba20c7b82
description: "Last modified: March 09, 2015"
---

# SERVICEWIZARDDLGPROC
 
**Applies to**: Outlook 
  
Defines a callback function invoked by the Profile Wizard to allow a service provider to react to user events when the provider's property sheets or pages are being shown. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiwz.h  <br/> |
|Defined function implemented by:  <br/> |Service providers  <br/> |
|Defined function called by:  <br/> |MAPI Profile Wizard  <br/> |
   
```cpp
BOOL SERVICEWIZARDDLGPROC(
  HWND hDlg,
  UINT wMsgID,
  WPARAM wParam,
  LPARAM lParam
);
```

## Parameters

_hDlg_
  
> [in] Window handle to the Profile Wizard dialog box. 
    
_wMsgID_
  
> [in] The window message to be processed. In addition to the regular window messages expected by a modal dialog box, the following messages can be received:
    
WM_CLOSE 
  
> The Profile Wizard has completed. The service provider should do all required cleanup such as deallocating any dynamically allocated memory. 
    
WM_COMMAND 
  
> One of the provider's controls has been selected, or the **Next** or **Back** button has been clicked. The value in the  _wParam_ parameter indicates which of these user events has occurred. 
    
WM_INITDIALOG 
  
> The user has moved to another property page, for which the dialog box must be initialized. The provider should initialize the controls that the Profile Wizard has added to the dialog box. 
    
WIZ_QUERYNUMPAGES 
  
> The Profile Wizard is prompting for the number of pages that the provider needs to display. The provider should return the number of pages instead of TRUE or FALSE. For example, use the following return statement to indicate that three pages should to be displayed:
    
   ```cpp
return (BOOL)3;

   ```

_wParam_
  
> [in] A 32-bit parameter associated with window messages. Possible values depend on the message specified in the  _wMsgID_ parameter. In addition to the values expected with the regular window messages for a modal dialog box, the following values can be received: 
    
WIZ_NEXT 
  
> When  _wMsgID_ contains WM_COMMAND, the user has clicked the **Next** button. 
    
WIZ_PREV 
  
> When  _wMsgID_ contains WM_COMMAND, the user has clicked the **Back** button. 
    
_lParam_
  
> [in] A 32-bit parameter associated with window messages. Possible values depend on the message specified in the  _wMsgID_ parameter. 
    
## Return value

The value returned by a **SERVICEWIZARDDLGPROC** based function is dependent on the window message received. Note in particular the exceptional return value for the WIZ_QUERYNUMPAGES message. The normal return values are: 
  
TRUE 
  
> The service provider has processed the received window message. 
    
FALSE 
  
> The service provider has not processed the received window message.
    
## Remarks

When the user moves from one property page to another, the provider is responsible for hiding the old page's controls and showing the controls for the next or previous page. When the user clicks the **Next** button, the **SERVICEWIZARDDLGPROC** based function is called with the WM_COMMAND message and WIZ_NEXT in the  _wParam_ parameter. The following steps describe what occurs between the time the user clicks **Next** and the time the first provider's configuration pages are rendered. 
  
1. The Profile Wizard hides any controls that are on the window. 
    
2. The Profile Wizard adds the provider's hidden controls to the page. 
    
3. The Profile Wizard calls **SERVICEWIZARDDLGPROC**, sending the WM_INITDIALOG message, so that the provider can initialize the controls. 
    
4. The Profile Wizard calls **SERVICEWIZARDDLGPROC**, sending the WIZ_QUERYNUMPAGES message. The provider returns the number of pages that are to be shown. 
    
5. The Profile Wizard calls **SERVICEWIZARDDLGPROC**, sending the WM_COMMAND message with the  _wParam_ parameter set to either WIZ_NEXT or WIZ_PREV. At this point, the provider either returns FALSE {error} or reveals its controls and returns TRUE {success}. If the Profile Wizard passes in ID_NEXT, the provider's first page is displayed. If ID_PREV is passed in, the last page is displayed. 
    
6. The Profile Wizard calls the provider's **SERVICEWIZARDDLGPROC** function, sending the WM_COMMAND message with the  _wParam_ parameter set to either WIZ_NEXT or WIZ_PREV (depending on which button the user clicked). The provider is responsible for showing or hiding its controls and writing its data to the **IMAPIProp** passed to the Profile Wizard to step through its sequence of pages. The provider should return TRUE if the next or previous page was successfully shown, and FALSE if neither the next nor previous page could be shown. The provider needs to be aware of when it is stepping outside of its sequence of pages, and respond appropriately by hiding its controls and writing its data to the profile. 
    
7. If the user steps outside the provider's range of pages, the Profile Wizard deletes the provider's hidden controls from the dialog box and calls the next provider or displays its next page if that was the last provider. 
    

