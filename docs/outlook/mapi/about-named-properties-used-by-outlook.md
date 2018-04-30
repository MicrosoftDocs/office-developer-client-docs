---
title: "About Named Properties Used by Outlook"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 8c245ec2-bb18-ecf0-b4ad-8c164c5924cf
description: "Last modified: June 25, 2012"
---

# About Named Properties Used by Outlook

 **Last modified:** June 25, 2012 
  
 * **Applies to:** Outlook * 
  
MAPI provides a facility for assigning names to certain properties, for mapping these names to unique identifiers, and for making this name-to-identifier mapping persistent across sessions. Named properties are identified by a name and a globally unique identifier (GUID) for a property set. The name can be a number or a string. For Microsoft Outlook 2013 or Microsoft Outlook 2010, the property set is often a namespace defined by Outlook 2013 or Outlook 2010, such as **PSETID_Appointment**. 
  
Named properties are manipulated by using the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) function and the [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md) function. The name and the property set GUID are passed to the [IMAPIProp::GetIDsFromNames](imapiprop-getidsfromnames.md) function to obtain a property identifier that is valid for the current MAPI session. Because this property identifier can vary from computer to computer, the only consistent way to access a named property is to know its name and property set GUID. The range for identifiers is always in the 0x8000 and 0xFFFE range. 
  
Any object that implements the [IMAPIProp : IUnknown](imapipropiunknown.md) interface can support named properties. Specifically, a MAPI service provider or a MAPI client must implement [IMAPIProp::GetProps](imapiprop-getprops.md) to get values of named properties. Setting named properties used by Outlook 2013 or Outlook 2010 is not supported because of the risk of corrupting data that is shared with other MAPI providers or clients. 
  
Outlook 2013 and Outlook 2010 use MAPI named properties to implement many of their features, for example, attachment security and meeting counter-proposals. Above this underlying data, Outlook 2013 and Outlook 2010 expose some of these properties as item properties in their Outlook 2013 and Outlook 2010 object models. For example, the **Email1Address** property of the **ContactItem** object in the object model corresponds to the named [PidLidEmail1EmailAddress Canonical Property](pidlidemail1emailaddress-canonical-property.md) in the **PSETID_Address** namespace. But in general, due to concerns for compatibility and data integrity, many of the MAPI properties that are used by Outlook 2013 and Outlook 2010 are not exposed in the object model. 
  
This reference describes a number of named properties that are listed below.
  
Named properties in the **PSETID_Address** namespace are the following: 
  
- [PidLidEmail1AddressType Canonical Property](pidlidemail1addresstype-canonical-property.md)
    
- [PidLidEmail1EmailAddress Canonical Property](pidlidemail1emailaddress-canonical-property.md)
    
- [PidLidEmail1OriginalEntryId Canonical Property](pidlidemail1originalentryid-canonical-property.md)
    
- [PidLidEmail2AddressType Canonical Property](pidlidemail2addresstype-canonical-property.md)
    
- [PidLidEmail2DisplayName Canonical Property](pidlidemail2displayname-canonical-property.md)
    
- [PidLidEmail2EmailAddress Canonical Property](pidlidemail2emailaddress-canonical-property.md)
    
- [PidLidEmail2OriginalDisplayName Canonical Property](pidlidemail2originaldisplayname-canonical-property.md)
    
- [PidLidEmail2OriginalEntryId Canonical Property](pidlidemail2originalentryid-canonical-property.md)
    
- [PidLidEmail3AddressType Canonical Property](pidlidemail3addresstype-canonical-property.md)
    
- [PidLidEmail3DisplayName Canonical Property](pidlidemail3displayname-canonical-property.md)
    
- [PidLidEmail3EmailAddress Canonical Property](pidlidemail3emailaddress-canonical-property.md)
    
- [PidLidEmail3OriginalDisplayName Canonical Property](pidlidemail3originaldisplayname-canonical-property.md)
    
- [PidLidEmail3OriginalEntryId Canonical Property](pidlidemail3originalentryid-canonical-property.md)
    
- [PidLidEmail1DisplayName Canonical Property](pidlidemail1displayname-canonical-property.md)
    
- [PidLidEmail1OriginalDisplayName Canonical Property](pidlidemail1originaldisplayname-canonical-property.md)
    
- [PidLidFileUnder Canonical Property](pidlidfileunder-canonical-property.md)
    
- [PidLidInstantMessagingAddress Canonical Property](pidlidinstantmessagingaddress-canonical-property.md)
    
- [PidLidWorkAddressCity Canonical Property](pidlidworkaddresscity-canonical-property.md)
    
- [PidLidWorkAddressCountry Canonical Property](pidlidworkaddresscountry-canonical-property.md)
    
- [PidLidWorkAddressPostalCode Canonical Property](pidlidworkaddresspostalcode-canonical-property.md)
    
- [PidLidWorkAddressPostOfficeBox Canonical Property](pidlidworkaddresspostofficebox-canonical-property.md)
    
- [PidLidWorkAddressState Canonical Property](pidlidworkaddressstate-canonical-property.md)
    
- [PidLidWorkAddressStreet Canonical Property](pidlidworkaddressstreet-canonical-property.md)
    
- [PidLidYomiCompanyName Canonical Property](pidlidyomicompanyname-canonical-property.md)
    
- [PidLidYomiFirstName Canonical Property](pidlidyomifirstname-canonical-property.md)
    
- [PidLidYomiLastName Canonical Property](pidlidyomilastname-canonical-property.md)
    
Named properties in the **PSETID_Appointment** namespace are the following: 
  
- [PidLidAllAttendeesString Canonical Property](pidlidallattendeesstring-canonical-property.md)
    
- [PidLidAppointmentCounterProposal Canonical Property](pidlidappointmentcounterproposal-canonical-property.md)
    
- [PidLidAppointmentDuration Canonical Property](pidlidappointmentduration-canonical-property.md)
    
- [PidLidAppointmentEndWhole Canonical Property](pidlidappointmentendwhole-canonical-property.md)
    
- [PidLidAppointmentStartWhole Canonical Property](pidlidappointmentstartwhole-canonical-property.md)
    
- [PidLidBusyStatus Canonical Property](pidlidbusystatus-canonical-property.md)
    
- [PidLidCcAttendeesString Canonical Property](pidlidccattendeesstring-canonical-property.md)
    
- [PidLidLocation Canonical Property](pidlidlocation-canonical-property.md)
    
- [PidLidRecurring Canonical Property](pidlidrecurring-canonical-property.md)
    
- [PidLidToAttendeesString Canonical Property](pidlidtoattendeesstring-canonical-property.md)
    
Named properties in the **PSETID_Common** namespace are the following: 
  
- [PidLidCommonEnd Canonical Property](pidlidcommonend-canonical-property.md)
    
- [PidLidCommonStart Canonical Property](pidlidcommonstart-canonical-property.md)
    
- [PidLidCompanies Canonical Property](pidlidcompanies-canonical-property.md)
    
- [PidLidContacts Canonical Property](pidlidcontacts-canonical-property.md)
    
- [PidLidCustomFlag Canonical Property](pidlidcustomflag-canonical-property.md)
    
- [PidLidFormPropStream Canonical Property](pidlidformpropstream-canonical-property.md)
    
- [PidLidFormStorage Canonical Property](pidlidformstorage-canonical-property.md)
    
- [PidLidHeaderItem Canonical Property](pidlidheaderitem-canonical-property.md)
    
- [PidLidPageDirStream Canonical Property](pidlidpagedirstream-canonical-property.md)
    
- [PidLidPropertyDefinitionStream Canonical Property](pidlidpropertydefinitionstream-canonical-property.md)
    
- [PidLidReminderSet Canonical Property](pidlidreminderset-canonical-property.md)
    
- [PidLidReminderTime Canonical Property](pidlidremindertime-canonical-property.md)
    
- [PidLidFlagRequest Canonical Property](pidlidflagrequest-canonical-property.md)
    
- [PidLidScriptStream Canonical Property](pidlidscriptstream-canonical-property.md)
    
- [PidLidSmartNoAttach Canonical Property](pidlidsmartnoattach-canonical-property.md)
    
- [PidLidToDoTitle Canonical Property](pidlidtodotitle-canonical-property.md)
    
- [PidLidUseTnef Canonical Property](pidlidusetnef-canonical-property.md)
    
Named properties in the **PSETID_Meeting** namespace are the following: 
  
- [PidLidMeetingType Canonical Property](pidlidmeetingtype-canonical-property.md)
    
Named properties in the **PSETID_Task** namespace are the following: 
  
- [PidLidTaskActualEffort Canonical Property](pidlidtaskactualeffort-canonical-property.md)
    
- [PidLidTaskDueDate Canonical Property](pidlidtaskduedate-canonical-property.md)
    
- [PidLidTaskEstimatedEffort Canonical Property](pidlidtaskestimatedeffort-canonical-property.md)
    
- [PidLidTaskFRecurring Canonical Property](pidlidtaskfrecurring-canonical-property.md)
    
- [PidLidTaskStartDate Canonical Property](pidlidtaskstartdate-canonical-property.md)
    
- [PidLidTaskStatus Canonical Property](pidlidtaskstatus-canonical-property.md)
    
Named properties in the **PS_INTERNET_HEADERS** namespace are the following: 
  
- [PidTagInternetReturnPath Canonical Property](pidtaginternetreturnpath-canonical-property.md)
    
Named properties in the **PSETID_Log** namespace are the following: 
  
- [PidLidLogDuration Canonical Property](pidlidlogduration-canonical-property.md)
    
- [PidLidLogEnd Canonical Property](pidlidlogend-canonical-property.md)
    
- [PidLidLogStart Canonical Property](pidlidlogstart-canonical-property.md)
    
- [PidLidLogType Canonical Property](pidlidlogtype-canonical-property.md)
    
Named properties in the **PS_PUBLIC_STRINGS** namespace are the following: 
  
- [PidNameKeywords Canonical Property](pidnamekeywords-canonical-property.md)
    
- [PidNameExchangeJunkEmailMoveStamp Canonical Property](pidnameexchangejunkemailmovestamp-canonical-property.md)
    
## See also

#### Concepts

[MAPI Constants](mapi-constants.md)
  
[How to: Determine if Outlook Downloaded Only the Header of a Message](how-to-determine-if-outlook-downloaded-only-the-header-of-a-message.md)
  
[How to: Get the Email Address of a Contact Item](how-to-get-the-email-address-of-a-contact-item.md)
  
[How to: Remove Custom Form Definition Saved With a Message](how-to-remove-custom-form-definition-saved-with-a-message.md)

