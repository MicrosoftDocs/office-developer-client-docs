---
title: "Property Entries in MapiSvc.inf Message Service Sections"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 714f99e2-80fc-4785-b707-611d8a6c229f
description: "Last modified: July 23, 2011"
 
 
---

# Property Entries in MapiSvc.inf Message Service Sections

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Entries that set properties use this format:
  
 **property tag** **=** property value 
  
The property tag can be a standard MAPI property tag if the configuration data represents one of the properties predefined by MAPI, or a nonstandard tag if the data does not represent a MAPI property. The nonstandard tag is made by combining the value for a property identifier with a property type. The result is an 8 digit hexadecimal number. The property value can be whatever makes sense for the property tag. 
  
Message service sections can contain a variety of entries depending on the message service being configured. The following MAPI properties are typically included in a message services section in the listed format:
  
 **PR_DISPLAY_NAME** =  _string_
  
 **PR_SERVICE_DLL_NAME** =  _name of DLL file_
  
 **PR_SERVICE_ENTRY_NAME** =  _name of entry point function_
  
 **PR_SERVICE_SUPPORT_FILES** =  _list of files_
  
 **PR_SERVICE_DELETE_FILES** =  _list of files_
  
 **PR_RESOURCE_FLAGS** =  _bitmask_
  
The **PR_DISPLAY_NAME** ([PidTagDisplayName](pidtagdisplayname-canonical-property.md)) string is the name of the message service that is shown in the user interface, the name that the user associates with the message service. The display name is an optional entry in mapisvc.inf. Sometimes the display name will be made up of two parts; a part assigned by the message service and a part assigned by the user. If the user is responsible for assigning one of the parts, this is typically handled with a special dialog box known as a property sheet supplied by the message service under the control of a client application. 
  
The information provided for the **PR_SERVICE_DLL_NAME** ([PidTagServiceDllName](pidtagservicedllname-canonical-property.md)) entry is the name of the DLL that contains the message service. The information provided for the **PR_SERVICE_ENTRY_NAME** ([PidTagServiceEntryName](pidtagserviceentryname-canonical-property.md)) entry is the name of the entry point function within that DLL that MAPI calls to configure the message service. 
  
The files listed in the **PR_SERVICE_SUPPORT_FILES** ([PidTagServiceSupportFiles](pidtagservicesupportfiles-canonical-property.md)) entry are files that must be installed with the message service. Likewise, the files in the **PR_SERVICE_DELETE_FILES** ([PidTagServiceDeleteFiles](pidtagservicedeletefiles-canonical-property.md)) entry must be removed when the message service is removed. 
  
The **PR_RESOURCE_FLAGS** ([PidTagResourceFlags](pidtagresourceflags-canonical-property.md)) entry is a collection of options defined for the message service. For example, the SERVICE_SINGLE_COPY bit is set when the message service can only appear once in a given profile. The SERVICE_NO_PRIMARY_IDENTITY bit is set if the message service does not provide identity information. 
  
Two examples of nonstandard property entries follow. The first entry specifies the path to the file used by the Default Address Book as the property value; the second entry specifies a numeric property value. Both entries have meaning specific to the AB message service.
  
```cpp
6600001e=full path to file
66040003=integer

```


