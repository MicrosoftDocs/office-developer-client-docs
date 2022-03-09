---
title: "ADRPARM"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ADRPARM
api_type:
- COM
ms.assetid: 35cd57b4-9901-456c-bf06-1f84e274eb4e
description: "Last modified: March 09, 2015"
---

# ADRPARM

**Applies to**: Outlook 2013 | Outlook 2016
  
Describes the display and behavior of the common address dialog box.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |

```cpp
typedef struct _ADRPARM
{
  ULONG cbABContEntryID;
  LPENTRYID lpABContEntryID;
  ULONG ulFlags;
  LPVOID lpReserved;
  ULONG ulHelpContext;
  LPSTR lpszHelpFileName;
  LPFNABSDI lpfnABSDI;
  LPFNDISMISS lpfnDismiss;
  LPVOID lpvDismissContext;
  LPSTR lpszCaption;
  LPSTR lpszNewEntryTitle;
  LPSTR lpszDestWellsTitle;
  ULONG cDestFields;
  ULONG nDestFieldFocus;
  LPSTR FAR *lppszDestTitles;
  ULONG FAR *lpulDestComps;
  LPSRestriction lpContRestriction;
  LPSRestriction lpHierRestriction;
} ADRPARM, FAR *LPADRPARM;

```

## Members

**cbABContEntryID**
  
> Count of bytes in the entry identifier pointed to by **lpABContEntryID**.

**lpABContEntryID**
  
> Pointer to the entry identifier of the container that supplies the initial list of recipient addresses that are displayed in the address dialog box.

**ulFlags**
  
> Bitmask of flags associated with various address dialog box options. The following flags can be set:

AB_RESOLVE
  
> Enable all names to be resolved after the address dialog box is closed. If there are ambiguous entries that result from the name resolution process, a dialog box appears to prompt the user for help in resolving them. Setting this flag guarantees that all of the names returned by [IAddrBook::Address](iaddrbook-address.md) are resolved.

AB_SELECTONLY
  
> Disable the creation of one-off addresses for a recipient list. This flag is used only if the dialog box is modal, as indicated by the DIALOG_MODAL flag being set.

ADDRESS_ONE
  
> The user can select exactly one recipient instead of multiple recipients from a list. This flag is valid only when **cDestFields** is zero and the dialog box is modal, as indicated by the DIALOG_MODAL flag being set.

DIALOG_MODAL
  
> Causes the modal version of the common address dialog box to be displayed. Either this flag or DIALOG_SDI should be set; they cannot both be set.

DIALOG_OPTIONS
  
> Causes the **Send Options** button to be displayed in the dialog box. This flag is used only if the dialog box is modal, as indicated by the DIALOG_MODAL flag being set.

DIALOG_SDI
  
> Causes the modeless version of the common address dialog box to be displayed. Either this flag or DIALOG_MODAL should be set; they cannot both be set. The DIALOG_SDI flag is ignored for non-Outlook clients, and the modal version of the dialog box will be displayed. Consequently, a pointer to a handle should not be expected in the _lpulUIParam_ parameter of [IAddrBook::Address](iaddrbook-address.md).

**lpReserved**
  
> Reserved, must be zero.

**ulHelpContext**
  
> Specifies the context within **Help** that will first be shown when the user clicks the Help button in the address dialog box.

**lpszHelpFileName**
  
> Pointer to the name of a Help file that will be associated with the address dialog box. The **lpszHelpFileName** member is used together with **ulHelpContext** to call the Windows **WinHelp** function.

**lpfnABSDI**
  
> Pointer to a MAPI function based on the [ACCELERATEABSDI](accelerateabsdi.md) prototype or NULL. This member applies to the modeless version of the dialog box only, as indicated by the DIALOG_SDI flag being set. Clients building an **ADRPARM** structure to pass to [IAddrBook::Address](iaddrbook-address.md) must always set the **lpfnABSDI** member to NULL. If the DIALOG_SDI flag is set, MAPI will then set it to a valid function before returning. Clients call this function from in their message loop to make sure that accelerators in the address book dialog box work. When the dialog box is dismissed and MAPI calls the function pointed to by the **lpfnDismiss** member, clients should unhook the **ACCELERATEABSDI** function from their message loop.

**lpfnDismiss**
  
> Pointer to a function based on the [DISMISSMODELESS](dismissmodeless.md) prototype or NULL. This member applies only to the modeless version of the dialog box only, as indicated by the DIALOG_SDI flag being set. MAPI calls the **DISMISSMODELESS** function when the user dismisses the modeless address dialog box, informing a client calling **IAddrBook::Address** that the dialog box is no longer active.

**lpvDismissContext**
  
> Pointer to context information to be passed to the **DISMISSMODELESS** function pointed to by the **lpfnDismiss** member. This member applies only to the modeless version of the dialog box, as indicated by the DIALOG_SDI flag being set.

**lpszCaption**
  
> Pointer to text to be used as the title for the common address dialog box.

**lpszNewEntryTitle**
  
> Pointer to text to be used as the button label for the button that invokes either the **New Entry** dialog box or another dialog box.

**lpszDestWellsTitle**
  
> Pointer to text to be used as a title for the recipient text box controls that can appear in the modal version of the common address dialog box. This member is not used for modeless dialog boxes.

**cDestFields**
  
> Count of recipient text box controls in the modal version of the address dialog box, or zero if the dialog box is modeless. The address dialog box is open for browsing only when the following conditions are true:

- The **cDestFields** member is set to zero.

- The DIALOG_BOX flag is set.

- The ADDRESS_ONE flag is not set.

  Setting **cDestFields** to 0XFFFFFFFF implies that MAPI should create the default number of recipient text box controls. In this case, the **lppszDestTitles** and **lpulDestComps** members must be NULL.

**nDestFieldFocus**
  
> Indicates the particular text box control that should have the initial focus when the modal version of the dialog box appears. This value must be between 0 and the value of **cDestFields** minus 1.

**lppszDestTitles**
  
> Pointer to an array of labels for buttons associated with each of the text box controls that are displayed in the modal version of the address dialog box. The value of the **cDestFields** member indicates the number of labels included in the array. If the **lppszDestTitles** member is NULL, the **Address** method uses default titles.

**lpulDestComps**
  
> Pointer to an array of recipient type values, such as MAPI_TO, MAPI_CC, and MAPI_BCC, that is associated with each text box control. The value of the **CDestFields** member indicates the number of recipient types included in the array. The values pointed to by **lpulDestComps** can be used to set the **PR_RECIPIENT_TYPE** ([PidTagRecipientType](pidtagrecipienttype-canonical-property.md)) property of each recipient. If the **lpulDestComps** member is NULL, the **Address** method uses default recipient types.

**lpContRestriction**
  
> Pointer to an [SRestriction](srestriction.md) structure that limits the type of address entries that can be displayed in the dialog box.

**lpHierRestriction**
  
> Pointer to an **SRestriction** structure that limits the address book containers that can supply address entries to be displayed in the dialog box.

## Remarks

**ADRPARM** structures are used by clients and service providers to control the appearance and behavior of the MAPI common address dialog boxes. There are two varieties of the address dialog box: modeless and modal. Some of the members in the **ADRPARM** structure apply to both versions of the dialog box, but some only apply to one of the two versions. The following table relates the members of an **ADRPARM** structure to their use with the common address dialog boxes.
  
|ADRPARM member|Type of dialog box|
|:-----|:-----|
|**cbABContEntryID** and **lpABContEntryID** <br/> |Modal and modeless  <br/> |
|**ulFlags** <br/> |Modal and modeless  <br/> |
|**lpReserved** <br/> |Modal and modeless  <br/> |
|**ulHelpContext** and **lpszHelpFileName** <br/> |Modal and modeless  <br/> |
|**lpfnABSDI** <br/> |Modeless  <br/> |
|**lpfnDismiss** and **lpvDismissContext** <br/> |Modeless  <br/> |
|**lpszCaption** <br/> |Modal and modeless  <br/> |
|**lpszNewEntryTitle** <br/> |Modal  <br/> |
|**lpszDestWellsTitle**, **cDestFields**, **nDestFieldFocus**, **lppszDestTitles**, and **lpulDestComps** <br/> |Modal  <br/> |
|**lpContRestriction** <br/> |Modal and modeless  <br/> |
|**lpHierRestriction** <br/> |Modal and modeless  <br/> |

The modeless dialog box is a read-only display of entries from one or more address book containers. The dialog box can display all entries from the selected containers or be limited to only those entries and containers that match criteria established by a restriction. The contents restriction pointed to by **lpContRestriction** can limit the types of entries displayed and the hierarchy restriction pointed to by **lpHierRestriction** can limit the containers providing the entries. To inform the caller when the dialog box is dismissed, MAPI invokes a function that is provided by the caller that matches the [DISMISSMODELESS](dismissmodeless.md) prototype. Another function, one that matches the [ACCELERATEABSDI](accelerateabsdi.md) prototype, is provided by MAPI and invoked by the caller in the Windows message loop to facilitate the working of keyboard shortcuts. The modeless version of the MAPI address dialog box can be displayed when clients call [IAddrBook::Address](iaddrbook-address.md) or when service providers call [IMAPISupport::Address](imapisupport-address.md).
  
The modal dialog box is a read/write display of entries from one or more containers. Its contents can be affected in the same manner as the modeless version by restrictions set in the **lpContRestriction** and **lpHierRestriction** members. In addition to the list box displaying container entries, the modal dialog box can contain between one and three text box controls for holding entries selected by the user. Each edit control is associated with a particular recipient type or **PR_RECIPIENT_TYPE** property such as MAPI_TO. The modal address dialog box can be displayed by either of the **Address** methods or when clients call [IAddrBook::Details](iaddrbook-details.md) and service providers call [IMAPISupport::Details](imapisupport-details.md).
  
This illustration includes two text box controls because the **cDestFields** member of the **ADRPARM** structure controlling the display of this dialog box is set to 2. The first control has initial focus because the **nDestFieldFocus** member is set to 0.
  
The **lpszNewEntryTitle** member points to text for a button label that, when it is selected, causes an additional dialog box to be displayed. Typically, as is shown in the illustration of the modal dialog box, the button is labeled **New** and the dialog box that appears lists all of the types of addresses that can be created by any of the address book providers in the profile. Clients cause this **New Entry** dialog box to be displayed by calling [IAddrBook::NewEntry](iaddrbook-newentry.md) and passing zero for the _cbEidNewEntryTpl_ parameter and NULL for the _lpEidNewEntryTpl_ parameter when the user selects the button. The information that is included in this dialog box comes from the MAPI one-off table.
  
Every entry in this dialog box is associated with a template for entering the data required to create an address of the particular type. Most address book providers supply one template for every type of address entry they can create. When a user makes a selection from this dialog box, MAPI displays the corresponding template.
  
The most significant four bits of the **ADRPARM** structure's **ulFlags** member contain a version number identifying the version of the **ADRPARM** structure. The current version is 0 (zero) or ADRPARM_HELP_CTX. The current implementation of MAPI will fail for any version of the structure other than zero.
  
Future versions of the structure may be completely different; they may not support the version-zero structure. The following macros are provided for extracting the version number from the **ulFlags** member and for combining it with the defined flags:
  
- **GET_ADRPARM_VERSION** (_ulFlags_)
- **SET_ADRPARM_VERSION** (_ulFlags_, _ulVersion_)
- **ADRPARM_HELP_CTX**
  
## See also

- [ACCELERATEABSDI](accelerateabsdi.md)
- [DISMISSMODELESS](dismissmodeless.md)
- [IAddrBook::Address](iaddrbook-address.md)
- [IMAPISupport::Address](imapisupport-address.md)
- [SRestriction](srestriction.md)
- [MAPI Structures](mapi-structures.md)
