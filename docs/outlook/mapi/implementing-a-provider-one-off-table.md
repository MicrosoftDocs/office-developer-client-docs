---
title: "Implementing a Provider One-Off Table"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 8b0dcbfe-6bed-4fb8-a906-009f1d009055 
---

# Implementing a Provider One-Off Table

**Applies to**: Outlook 2013 | Outlook 2016
 
MAPI calls your provider's [IABLogon::GetOneOffTable](iablogon-getoneofftable.md) method when the user of a client application adds a recipient to an outgoing message. Typically, the types of addresses requested are unique to your messaging system. If your provider supports recipient creation, it must supply a one-off table that exposes templates for every type of supported recipient address. If your provider does not support recipient creation, return MAPI_E_NO_SUPPORT from the **GetOneOffTable** call.
 
MAPI will typically keep your provider's one-off table open for the lifetime of the session, releasing it only when a client calls either the subsystem's or address book's [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method. MAPI registers for notifications on this table so that if templates are added or deleted, these changes can be reflected to the user.
 
 **To implement IABLogon::GetOneOffTable**
 
1. Check the value of the flags parameter, _ulFlags_. If the MAPI_UNICODE flag is set and your provider does not support Unicode, fail and return MAPI_E_BAD_CHARWIDTH.

2. Check if your provider's one-off table has already been created. Because one-off tables are typically static, your provider never has to go through the creation process more than once. If a table already exists, return a pointer to it.

3. If a one-off table does not yet exist, call **CreateTable** to create one.

4. Set the following properties for the columns in your table rows:

- **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) to the name of the type of recipient that the template can create.

- **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) to the entry identifier for the one-off template.

- **PR_DEPTH** ([PidTagDepth](pidtagdepth-canonical-property.md)) to indicate the hierarchy level in the one-off table display.

- **PR_SELECTABLE** ([PidTagSelectable](pidtagselectable-canonical-property.md)) to TRUE to indicate if the row represents a template and FALSE otherwise.

- **PR_ADDRTYPE** ([PidTagAddressType](pidtagaddresstype-canonical-property.md)) to the type of address created by the template.

- **PR_DISPLAY_TYPE** ([PidTagDisplayType](pidtagdisplaytype-canonical-property.md)) to DT_MAILUSER or another value that indicates the type of display for the template.

- **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md)) to a unique binary value.

5. Call [ITableData::HrModifyRow](itabledata-hrmodifyrow.md) to modify the table directly.

6. Call [ITableData::HrGetView](itabledata-hrgetview.md) to create an **IMAPITable** interface implementation to return to the caller.
