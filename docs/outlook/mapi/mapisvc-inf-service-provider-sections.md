---
title: "MapiSvc.inf Service Provider Sections"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: ab17dcf2-409b-4a57-9cc4-5794f995cd3e
description: "Last modified: July 23, 2011"
---

# MapiSvc.inf Service Provider Sections

**Applies to**: Outlook 2013 | Outlook 2016 
  
Mapisvc.inf includes one service provider section for each of the entries listed in the **Providers** entry in the preceding message services section. **Service** provider sections are similar to message service sections in that both types of sections contain entries in this format: 
  
**property tag** = property value 
  
However, service provider sections and message service sections differ in that such property entries are the only type of entry included in service provider sections. There can be no additional or linked sections for service providers; all service provider information must be contained within the one section. 
  
Some of the properties set in message service sections are also set in service provider sections because these properties make sense for both. The **PR_DISPLAY_NAME** property is an example. Both service providers and message services have a name that is used for display in the configuration user interface. Depending on the service provider, that name may or may not be the same. Other properties are specific to service providers. 
  
Typical service provider sections include the following entries, all of which are required:
  
**PR_DISPLAY_NAME** =  _string_
  
**PR_PROVIDER_DISPLAY** =  _string_
  
**PR_PROVIDER_DLL_NAME** =  _name of DLL file_
  
**PR_RESOURCE_TYPE** =  _long_
  
**PR_RESOURCE_FLAGS** =  _bitmask_
  
The **PR_PROVIDER_DLL_NAME** ([PidTagProviderDllName](pidtagproviderdllname-canonical-property.md)) entry is similar to **PR_SERVICE_DLL_NAME**; it indicates the filename for the DLL that contains the service provider. Message service code may be stored with one of its service providers in the same DLL file or exist as a separate DLL. Note that no suffix is included in the entry regardless of the target platform; MAPI takes care of adding a suffix if necessary. 
  
**PR_RESOURCE_TYPE** ([PidTagResourceType](pidtagresourcetype-canonical-property.md)) entry represents the type of service provider; service providers set it to the appropriate predefined constant. Valid values include MAPI_STORE_PROVIDER, MAPI_TRANSPORT_PROVIDER, and MAPI_AB_PROVIDER.
  
Another property entry that applies to both message services and service providers, the **PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) entry indicates options. The settings for this property entry can differ depending on the service provider. For example, some message store providers might set **PR_RESOURCE_FLAGS** to STATUS_NO_DEFAULT_STORE if they can never operate as the default message store. 
  
Three examples of service provider sections follow. The **[AB Provider]** section is the service provider section for the Default Address Book service. The **[MsgService Prov1]** and **[MsgService Prov2]** sections belong to My Own Service; the first is an address-book provider section and the second is a message-store provider section. 
  
```cpp
[AB Provider]
PR_DISPLAY_NAME=Default Address Book
PR_PROVIDER_DISPLAY=Default Address Book
PR_PROVIDER_DLL_NAME=AB.DLL
PR_RESOURCE_TYPE=MAPI_AB_PROVIDER
6600001e=C:\WINNT35\System32\DEFAB.TXT
[MsgService Prov1]
PR_DISPLAY_NAME=My Own Service
PR_PROVIDER_DISPLAY=My Own Address Book
PR_PROVIDER_DLL_NAME=MYXXX.DLL
PR_RESOURCE_TYPE=MAPI_AB_PROVIDER
[MsgService Prov2]
PR_DISPLAY_NAME=My Folders
PR_PROVIDER_DISPLAY=My Own Message Store
PR_RESOURCE_TYPE=MAPI_STORE_PROVIDER
PR_PROVIDER_DLL_NAME=MYZZZ.DLL
PR_RESOURCE_FLAGS=STATUS_NO_DEFAULT_STORE
66060003=00000000
66030003=00000000
34140102=78b2fa70aff711cd9bc800aa002fc45a
66090003=06000000
660A0003=03000000

```


