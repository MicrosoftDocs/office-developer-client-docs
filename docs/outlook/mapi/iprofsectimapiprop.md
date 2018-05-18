---
title: "IProfSect  IMAPIProp"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProfSect
api_type:
- COM
ms.assetid: 4e704044-5230-4521-a0d2-b7c2f981c954
description: "Last modified: March 09, 2015"
---

# IProfSect : IMAPIProp

  
  
**Applies to**: Outlook 
  
Works with the properties of profile section objects. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Exposed by:  <br/> |Profile section objects  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
|Interface identifier:  <br/> |IID_IProfSect  <br/> |
|Pointer type:  <br/> |LPPROFSECT  <br/> |
|Transaction model:  <br/> |Nontransacted  <br/> |
   
## Vtable order

This interface does not have any unique methods.
  
|**Required properties**|**Access**|
|:-----|:-----|
|**PR_OBJECT_TYPE** ([PidTagObjectType](pidtagobjecttype-canonical-property.md))  <br/> |Read-only  <br/> |
|**PR_PROFILE_NAME** ([PidTagProfileName](pidtagprofilename-canonical-property.md))  <br/> |Read-only  <br/> |
   
## Notes to callers

The **IProfSect** interface does not have any unique methods of its own, but you can call the profile section's [IMAPIProp](imapipropiunknown.md) methods. There are some differences between the **IProfSect** implementation and other implementations of **IMAPIProp**:
  
- **IProfSect** does not support a transaction model. 
    
- **IProfSect** does not support named properties. 
    
- **IProfSect** reserves the identifier range 0x67F0 to 0x67ff for secure properties. 
    
Not supporting a transaction model means that all changes that were made to a profile section following calls to the [IMAPIProp::CopyProps](imapiprop-copyprops.md) and [IMAPIProp::CopyTo](imapiprop-copyto.md) methods occur immediately. Calls to the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method succeed but do not actually save any changes. 
  
To be protected from changes that occur prematurely, service providers need to make copies of their profile sections that are displayed to users through property sheets. The property sheets should work with the copy, instead of the real profile section. When the user clicks the **OK** button to verify that the changes are accurate, the changes can be saved to the real profile section. 
  
To implement a property sheet by using a copied profile section, use the following procedure:
  
1. Open the profile section by calling the [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) or [IProviderAdmin::OpenProfileSection](iprovideradmin-openprofilesection.md) method. 
    
2. Call the [CreateIProp](createiprop.md) function to retrieve a property data object — an object that supports the **IPropData** interface. 
    
3. Call the profile section's [IMAPIProp::CopyTo](imapiprop-copyto.md) method to copy the properties that will appear on the property sheet from the profile section to the property data object. 
    
4. Call the [IMAPISupport::DoConfigPropSheet](imapisupport-doconfigpropsheet.md) method to request that the service provider display a property sheet, and pass a pointer to the property data object in the  _lpConfigData_ parameter. 
    
5. When the user saves changes to configuration properties in the property sheet, call the [IMAPIProp::CopyTo](imapiprop-copyto.md) method to copy the properties from the property data object back to the profile section. 
    
Profile sections, unlike other objects, do not support named properties. The [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) and [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) methods return MAPI_E_NO_SUPPORT if they are called on a profile section object. If you use the [IMAPIProp::SetProps](imapiprop-setprops.md) method to set property identifiers in the range above 0x8000, the PT_ERROR property type will be returned. 
  
Profile sections reserve the identifier range 0x67F0 to 0x67FF for secure properties. Service providers can use this range to store passwords and other provider-specific credentials. Properties in this range are not returned in the complete list of properties when NULL is passed in the  _lpPropTag_ parameter of the [IMAPIProp::GetProps](imapiprop-getprops.md) method, nor are they returned in the  _lppPropTagArray_ parameter of the [IMAPIProp::GetPropList](imapiprop-getproplist.md) method. Secure properties must be requested specifically by their identifiers. 
  
MAPI furnishes a profile section with the hard-coded constant MUID_PROFILE_INSTANCE as its identifier and **PR_SEARCH_KEY** ([PidTagSearchKey](pidtagsearchkey-canonical-property.md)) as its single property. MAPI ensures that the **PR_SEARCH_KEY** property value will be unique among all created profiles. Use **PR_SEARCH_KEY** instead of **PR_PROFILE_NAME** when uniqueness is important, because it is possible for a deleted profile to be followed by another profile with the same name. 
  
For more information about how to use profile sections, see [Administering Profiles and Message Services](administering-profiles-and-message-services.md).
  
## See also



[MAPI Interfaces](mapi-interfaces.md)

