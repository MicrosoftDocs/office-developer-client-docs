---
title: "PidLidPostalAddressId Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidPostalAddressId
api_type:
- COM
ms.assetid: 30fdfb20-1e12-442a-bfa0-8c18c15fa5c3
description: "Last modified: March 09, 2015"
---

# PidLidPostalAddressId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Specifies which physical address is the contact's mailing address.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidPostalAddressId  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x00008022  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

If present, this property must have one of the values that are specified in the table below or in [[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx). If not set, the application should assume that the value is "0x00000000".
  
|**Value**|**Description**|
|:-----|:-----|
|0x00000000  <br/> |No address is selected as the mailing address. **PR_STREET_ADDRESS** ([PidTagStreetAddress](pidtagstreetaddress-canonical-property.md)), **PR_LOCALITY** ([PidTagLocality](pidtaglocality-canonical-property.md)), **PR_STATE_OR_PROVINCE** ([PidTagStateOrProvince](pidtagstateorprovince-canonical-property.md)), **PR_POSTAL_CODE** ([PidTagPostalCode](pidtagpostalcode-canonical-property.md)), **PR_COUNTRY** ([PidTagCountry](pidtagcountry-canonical-property.md)), **dispidAddressCountryCode** ([PidLidAddressCountryCode](pidlidaddresscountrycode-canonical-property.md)), and **PR_POSTAL_ADDRESS** ([PidTagPostalAddress](pidtagpostaladdress-canonical-property.md)) all must not be set. |
|0x00000001  <br/> |The Home Address is the mailing address. The values of the **PR_STREET_ADDRESS**, **PR_LOCALITY**, **PR_STATE_OR_PROVINCE**, **PR_POSTAL_CODE**, **PR_POST_OFFICE_BOX** ([PidTagPostOfficeBox](pidtagpostofficebox-canonical-property.md)), **PR_COUNTRY**, **dispidAddressCountryCode**, and **PR_POSTAL_ADDRESS** properties must be equal to the values of the **PR_HOME_ADDRESS_STREET** ([PidTagHomeAddressStreet](pidtaghomeaddressstreet-canonical-property.md)), **PR_HOME_ADDRESS_CITY** ([PidTagHomeAddressCity](pidtaghomeaddresscity-canonical-property.md)), **PR_HOME_ADDRESS_STATE_OR_PROVINCE** ([PidTagHomeAddressStateOrProvince](pidtaghomeaddressstateorprovince-canonical-property.md)), **PR_HOME_ADDRESS_POSTAL_CODE** ([PidTagHomeAddressPostalCode](pidtaghomeaddresspostalcode-canonical-property.md)), **PR_HOME_ADDRESS_POST_OFFICE_BOX** ([PidTagHomeAddressPostOfficeBox](pidtaghomeaddresspostofficebox-canonical-property.md)), **PR_HOME_ADDRESS_COUNTRY** ([PidTagHomeAddressCountry](pidtaghomeaddresscountry-canonical-property.md)), **dispidHomeAddressCountryCode** ([PidLidHomeAddressCountryCode](pidlidhomeaddresscountrycode-canonical-property.md)), and **dispidHomeAddress** ([PidLidHomeAddress](pidlidhomeaddress-canonical-property.md)) properties, respectively. |
|0x00000002  <br/> |The Work Address is the mailing address. The values of the **PR_STREET_ADDRESS**, **PR_LOCALITY**, **PR_STATE_OR_PROVINCE**, **PR_POSTAL_CODE**, **PR_POST_OFFICE_BOX**, **PR_COUNTRY**, **dispidAddressCountryCode**, and **PR_POSTAL_ADDRESS** properties must be equal to the values of the **dispidWorkAddressStreet** ([PidLidWorkAddressStreet](pidlidworkaddressstreet-canonical-property.md)), **dispidWorkAddressCity** ([PidLidWorkAddressCity](pidlidworkaddresscity-canonical-property.md)), **dispidWorkAddressState** ([PidLidWorkAddressState](pidlidworkaddressstate-canonical-property.md)), **dispidWorkAddressPostalCode** ([PidLidWorkAddressPostalCode](pidlidworkaddresspostalcode-canonical-property.md)), **dispidWorkAddressPostOfficeBox** ([PidLidWorkAddressPostOfficeBox](pidlidworkaddresspostofficebox-canonical-property.md)), **dispidWorkAddressCountry** ([PidLidWorkAddressCountry](pidlidworkaddresscountry-canonical-property.md)), **dispidWorkAddressCountryCode** ([PidLidWorkAddressCountryCode](pidlidworkaddresscountrycode-canonical-property.md)), and **dispidWorkAddress** ([PidLidWorkAddress](pidlidworkaddress-canonical-property.md)) properties, respectively. |
|0x00000003  <br/> |The Other Address is the mailing address. The values of the, **PR_STREET_ADDRESS**, **PR_LOCALITY**, **PR_STATE_OR_PROVINCE**, **PR_POSTAL_CODE**, **PR_POST_OFFICE_BOX**, **PR_COUNTRY**, **dispidAddressCountryCode**, and **PR_POSTAL_ADDRESS** properties must be equal to the values of the **PR_OTHER_ADDRESS_STREET** ([PidTagOtherAddressStreet](pidtagotheraddressstreet-canonical-property.md)), **PR_OTHER_ADDRESS_CITY** ([PidTagOtherAddressCity](pidtagotheraddresscity-canonical-property.md)), **PR_OTHER_ADDRESS_STATE_OR_PROVINCE** ([PidTagOtherAddressStateOrProvince](pidtagotheraddressstateorprovince-canonical-property.md)), **PR_OTHER_ADDRESS_POSTAL_CODE** ([PidTagOtherAddressPostalCode](pidtagotheraddresspostalcode-canonical-property.md)), **PR_OTHER_ADDRESS_POST_OFFICE_BOX** ([PidTagOtherAddressPostOfficeBox](pidtagotheraddresspostofficebox-canonical-property.md)), **dispidOtherAddressCountryCode** ([PidLidOtherAddressCountryCode](pidlidotheraddresscountrycode-canonical-property.md)), and **dispidOtherAddress** ([PidLidOtherAddress](pidlidotheraddress-canonical-property.md)) properties, respectively. |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

