---
title: "What's New in This Edition"
manager: soliver
ms.date: 2/09/2020
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a24cad75-1237-469f-b7f3-cbbb88f80d44
description: "Last modified: February 09, 2020"
 
 
---

# What's New in This Edition

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The Microsoft Outlook MAPI Reference has been updated to include documentation for various new features. 
  
## New Content

Content has been added for the following features:
  
- The topic [Getting Started with the Outlook 2013 MAPI Reference](getting-started-with-the-outlook-mapi-reference.md) has been updated to reference comprehensive information about programming models for your Outlook and MAPI functionality to help you identify the APIs and technologies that are most appropriate for your needs. Links to the referenced Technical Article have also been revised in the following topics: 
    
  - [Outlook MAPI Reference](outlook-mapi-reference.md)
    
  - [Outlook MAPI Reference Overview](outlook-mapi-reference-overview.md)
    
- **Message Store Provider Example**—The [Sample Wrapped PST Store Provider](message-store-provider-sample.md) code has now been revised to recognize and accommodate Outlook 2013. For more information, see Previously Revised Content in this topic. 
    
- **Autocomplete Stream**—The [Nickname cache](nickname-cache.md) topic, formerly the **Nk2 File Format**, had been updated to reflect changes in Outlook 2013 as well as Outlook 2010. The following topics have now been revised to provide information about the .nk2 file format developer guidelines for Microsoft Outlook 2003/Microsoft Office Outlook 2007 and binary file parsing. For more information, see Previously Revised Content in this topic.
    
  - [MAPI Profiles](mapi-profiles.md)
    
  - [Nickname cache](nickname-cache.md)
    
  - [Autocomplete Stream](autocomplete-stream.md)
    
- **Interfaces**-The [IAddrBook::OpenEntry](iaddrbook-openentry.md) topic documents a method of opening an address book entry and returning a pointer to the interface used to access it. It previously contained a flag in the  *ulFlags*  parameter, **MAPI_GAL_ONLY**, which could be used to open the Global Address List (GAL), only, and has been revised to include its definition.
    
- **Properties**—The **PR_CONVERSATION_KEY** named property ([PidTagConversationKey Canonical Property](pidtagconversationkey-canonical-property.md)) topic has been added and relates to **IPM.MessageManager** messages in Outlook MAPI only. The following topics relating to it and the Transport-Neutral Encapsulation Format (TNEF) stream documentation have been revised: 
    
  - [Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
    
  - [Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)
    
  - [Mapping of TNEF Attributes to MAPI Properties](mapping-of-tnef-attributes-to-mapi-properties.md)
    
  - [attConversationID and attParentID](attconversationid-and-attparentid.md)
  
## MAPI Initialization Monitor  

- There are times when an application which consumes MAPI might want to know when the initialization is completed. For example, it have multiple threads which could initialize MAPI, or in response to MAPI being initialize the application would like perform some work, but does not want to always spin up the MAPI stack.  The initialization monitor provides this functionality through a function (exported from OLMAPI32.DLL) and a couple of simple interfaces described below. 

### HRESULT STDAPICALLTYPE CreateMapiInitializationMonitor(IMAPIInitMonitor ppInitMonitor) 

- This is entry point exported from OLMAPI32.DLL this allows the caller to retrieve an interface to query the current initialization state, setup a callback for initialization completion or block the current thread until has completed.  The object returned from this API is reusable and thread safe and can be invoked from any thread, not just thread which retrieved it.  Also, unlike other objects exposed from MAPI, this object is valid as long as the DLL is loaded, it can be re-used across initialization sessions and can be consumed before or after MAPIInitialize has been called. Returns success or failure through an COM standard HRESULT, and assigns an out parameter to an instance of IMAPIInitMonitor. 

### Interface: IMAPIInitMonitor 

**IFACEMETHODIMP_(BOOL) IsInitialized()**
- Returns the current state of MAPI initialization 

**IFACEMETHODIMP Wait(DWORD timeout)**
- Initiates a BLOCKING call on this thread, which will return either when the specified number of milliseconds have elapsed or MAPI has been initialized.  INFINITE can be used to for an infinite wait. 

**IFACEMETHODIMP BeginWait(DWORD timeout, IMAPIWaitResult ppResult)**
- Start a wait for MAPI initialization or the specified number of milliseconds to elapse.   This return an IMAPIWaitResult interface which should have “End” called in order begin the wait.  This allows the caller to control which thread is blocked while we are waiting. 

### Interface IMAPIWaitResult
**IFACEMETHODIMP End() override**
- Called to initiate the blocking wait on the thread where it is called, does not need to be the same thread that called “BeginWait”. 

    
## Previously Revised Content

Content was added in previous releases of the Outlook MAPI Reference for the following features:
  
- Microsoft Outlook 2013 allows for non-traditional deployment scenarios such as side-by-side and Click-to-Run. These scenarios can complicate the logic used to load the proper MAPI library. MAPI developers now have the option of linking explicitly to MAPI functions, and can choose to explicitly link to the MAPI stub of the default MAPI client (for example, Msmapi32.dll of Outlook) without going through the MAPI library and the Windows MAPI stub. For more information about explicit linking as compared with implicit linking, see [Link to MAPI Functions](how-to-link-to-mapi-functions.md). The **MAPI Stub Library**, posted on the [CodePlex](https://mapistublibrary.codeplex.com/) website, provides a drop-in replacement for Mapi32.lib that supports building both 32-bit and 64-bit MAPI applications. 
    
- **Support for 64-bit Microsoft Outlook**—Reference topics for applicable API elements were updated to correspond to new header files that support 64-bit Outlook. Those header files are available as a download at [Outlook 2010: MAPI Header Files](https://www.microsoft.com/downloads/details.aspx?FamilyID=f8d01fc8-f7b5-4228-baa3-817488a66db1). A new code sample was provided in [Check the Version of Outlook](how-to-check-the-version-of-outlook.md) to show how to check whether the installed version of Outlook is 64-bit Microsoft Outlook 2010 and has been revised for Outlook 2013. If your existing 32-bit MAPI application is going to be running on a 64-bit operating system with 64-bit Outlook installed, you will need to rebuild your 32-bit application as a 64-bit application. For more information about MAPI support for 64-bit Outlook, see [Building MAPI Applications on 32-Bit and 64-Bit Platforms](building-mapi-applications-on-32-bit-and-64-bit-platforms.md).
    
- **Message Store Provider Example**—The [Sample Wrapped PST Store Provider](message-store-provider-sample.md) had previously been updated to support 64-bit architecture. The Example's [Initializing a Wrapped PST Store Provider](initializing-a-wrapped-pst-store-provider.md) topic has now been expanded to provide information about the "Wrapped PST and Unicode Paths." 
    
- **Autocomplete Stream**—The [Nickname cache](nickname-cache.md) topic, formerly the **Nk2 File Format**, has been updated to reflect changes in Outlook 2013 as well as Outlook 2010. Information such as the autocomplete list, which is the list of names that displays in the **To**, **Cc**, and **Bcc** edit boxes while a user is composing an email, is now saved to the [Autocomplete Stream](autocomplete-stream.md) of a message on the local computer rather than saving it to a file as in Outlook 2007. 
    
  - Interacting with the Autocomplete Stream
    
  - Loading the Autocomplete Stream
    
  - Saving the Autocomplete Stream
    
- **Fast shutdown support for MAPI clients**—MAPI clients can now initiate a quick shutdown and have the MAPI subsystem notify loaded providers to minimize data loss from the fast shutdown. Additional interfaces were added for the client and provider to support fast shutdown. For more information about fast shutdown, see [Client Shutdown in MAPI](client-shutdown-in-mapi.md).
    
- **Stream structure for field definitions for an Outlook item**—Documentation for a binary stream for the [PidLidPropertyDefinitionStream](pidlidpropertydefinitionstream-canonical-property.md) property was added. This property specifies definitions of all custom fields and data-binding settings for built-in fields of an Outlook item. 
    
- **Personal Store Override**—The following interfaces and their respective methods were added to support overriding the Personal Folders file (PST) store providers **PSTDisableGrow** policy: 
    
    [IPSTOVERRIDEREQ::IUnknown](ipstoverridereqiunknown.md)
    
    [IPSTOVERRIDE1::IUnknown](ipstoverride1iunknown.md)
    
- **Using Multiple Exchange Accounts**—Documentation for the [MAPI Address Book API](using-multiple-exchange-accounts.md) was added. This API was enhanced to support multiple Exchange accounts in Microsoft Outlook 2010 and now includes Microsoft Outlook 2013. To resolve addresses correctly with multiple Exchange accounts, use the new functions that take an account context so that calls to the address book search the correct Exchange account. 
    
- **MAPI File Formats**—MAPI configuration information has been expanded to explain how you can use paths in [Registering Services and Service Providers in MapiSvc.inf](registering-services-and-service-providers-in-mapisvc-inf.md).
    
- **Properties**—The following tagged properties were added in addition to documentation for 38 other tagged properties and named properties that had previously been added:
    
  - [PidTagAddressBookChooseDirectoryAutomatically](pidtagaddressbookchoosedirectoryautomatically-canonical-property.md)
    
  - [PidTagAssociatedSharingProvider](pidtagassociatedsharingprovider-canonical-property.md)
    
  - [PidTagRoamingBinary](pidtagroamingbinary-canonical-property.md)
    
  - [PidTagSenderSmtpAddress](pidtagsendersmtpaddress-canonical-property.md)
    
  - [PidTagSentRepresentingSmtpAddress](pidtagsentrepresentingsmtpaddress-canonical-property.md)
    
  - [PidTagStoreEntryIdEmsmdbV1](pidtagstoreentryidemsmdbv1-canonical-property.md)
    
- **MAPI Constants**—The consolidated [MAPI Constants](mapi-constants.md) have been expanded. In previous releases, they were distributed in a number of topics but are now collected in a single topic to make them easier to discover and use. They have also been expanded to provide more extensive coverage including the following sections: 
    
  - Definitions for Exchange Address Book and Message Store Error Codes
    
  - Definitions for Exchange Server Mailbox Cached Mode Quotas
    
## See also



[Getting Started with the Outlook MAPI Reference](getting-started-with-the-outlook-mapi-reference.md)
  
[CodePlex](https://mapistublibrary.codeplex.com/)

