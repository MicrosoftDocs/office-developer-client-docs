---
title: "About Registering Stores for Indexing"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
localization_priority: Normal
ms.assetid: dd2aa06a-96e8-1291-18b5-fc3c40b74e4d
description: "Last modified: March 09, 2015"
 
 
---

# About Registering Stores for Indexing

  
  
**Applies to**: Outlook 
  
This topic is specific to Instant Search in Microsoft Office Outlook 2007.
  
Instant Search lets you quickly find items in Outlook. It uses components of Windows Desktop Search.
  
The MAPI Protocol Handler checks the Windows registry for stores that it should index for search purposes. Store providers that want to be indexed must be registered in the Windows registry.
  
By default, Windows Desktop Search adds the following four types of store providers to the Windows registry to allow indexing:
  
- Store for Personal Folders files (.PST).
    
-  Microsoft Exchange store, including any Offline Folder files (.ost). 
    
-  Store for public folders. 
    
-  Store for Microsoft Office Outlook Connector for MSN. 
    
 Third-party store providers that want to be indexed must register themselves in the Windows registry. 
  
> [!NOTE]
> Administrators and users can use a Group Policy setting to prevent Windows Desktop Search from indexing Outlook items. For more information, see [Extending Windows Desktop Search](http://msdn.microsoft.com/library/2eab146a-8516-4b95-b73c-ca7f980ba233%28Office.15%29.aspx). 
  
## Registry Keys

On a computer, all store providers that want to be indexed must be registered under only one of the following three registry keys in the Windows registry. The MAPI Protocol Handler looks under each of these keys in the following order:
  
1. [HKLM]\Software\Policies\Microsoft\Windows\Windows Search\
    
2. [HKLM]\Software\Microsoft\Windows\Windows Search\Preferences\
    
3. [HKCU]\Software\Microsoft\Windows\Windows Search\Preferences\
    
 Each value under the key corresponds to a store provider that would be indexed. The name of the value is the Globally Unique Identifier (GUID) of the store provider, which is of the type **DWORD** and has the hexadecimal value 0x00000001. 
  
## GUIDs for Store Providers

The MAPI property **[PR_MDB_PROVIDER](pidtagstoreprovider-canonical-property.md)** specifies the GUID of a MAPI store. The GUIDs for the store providers that Outlook indexes are described in the following table. 
  
||||
|:-----|:-----|:-----|
|**Type of Store Provider** <br/> |**GUID** <br/> |**Notes** <br/> |
|Personal Folders files (.PST)  <br/> |{4154494E-BFF9-01B8-00AA-0037D96E0000}  <br/> |GUID is documented in the public header file mspst.h as **MSPST_UID_PROVIDER** <br/> |
|Exchange  <br/> |{C0A19454-7F29-1B10-A587-08002B2A2517}  <br/> |GUID is documented in the public header file edkmdb.h as **pbExchangeProviderPrimaryUserGuid** <br/> |
|Public folders  <br/> |{70fab278-f7af-cd11-9bc8-00aa002fc45a}  <br/> |GUID is documented in the public header file edkmdb.h as **pbExchangeProviderPublicGuid** <br/> |
|Outlook Connector for MSN  <br/> |{c34f5c97-eb05-bb4b-b199-2a7570ec7cf9}  <br/> |None  <br/> |
   
## See also



[About the Store API](about-the-store-api.md)

